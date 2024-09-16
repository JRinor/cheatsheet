## Installation d'un runner GitLab en local

### Prérequis

- Un système Linux (Ubuntu/Debian recommandé)
- Accès root ou sudo
- Docker installé (optionnel mais recommandé pour l'exécuteur Docker)
- Git installé

### Étapes d'installation

1. **Ajout du dépôt officiel GitLab**

```bash
curl -L "https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh" | sudo bash
```

2. **Installation du package GitLab Runner**

```bash
sudo apt-get install gitlab-runner
```

3. **Vérification de l'installation**

```bash
gitlab-runner --version
```

### Enregistrement du runner

1. **Récupération des informations nécessaires**
   - URL de votre instance GitLab (ex: https://gitlab.com/)
   - Token d'enregistrement du runner (depuis les paramètres CI/CD du projet ou du groupe)

2. **Lancement de l'enregistrement**

```bash
sudo gitlab-runner register
```

3. **Répondez aux questions interactives**
   - URL de l'instance GitLab
   - Token d'enregistrement
   - Description du runner (ex: "runner-local")
   - Tags (optionnels, séparés par des virgules)
   - Executor (choisissez parmi shell, docker, docker-ssh, parallels, virtualbox, docker+machine, docker-ssh+machine, kubernetes)

4. **Pour un enregistrement non-interactif (optionnel)**

```bash
sudo gitlab-runner register \
  --non-interactive \
  --url "https://gitlab.com/" \
  --registration-token "VOTRE_TOKEN" \
  --executor "docker" \
  --docker-image alpine:latest \
  --description "runner-docker-local" \
  --tag-list "docker,aws" \
  --run-untagged="true" \
  --locked="false" \
  --access-level="not_protected"
```

### Configuration avancée

Éditez le fichier de configuration pour des réglages personnalisés :

```bash
sudo nano /etc/gitlab-runner/config.toml
```

Exemple de configuration pour un exécuteur Docker :

```toml
[[runners]]
  name = "runner-docker-local"
  url = "https://gitlab.com/"
  token = "VOTRE_TOKEN"
  executor = "docker"
  [runners.docker]
    tls_verify = false
    image = "alpine:latest"
    privileged = false
    disable_entrypoint_overwrite = false
    oom_kill_disable = false
    disable_cache = false
    volumes = ["/cache"]
    shm_size = 0
```

### Démarrage et gestion du service

```bash
# Démarrer le service
sudo systemctl start gitlab-runner

# Activer le démarrage automatique
sudo systemctl enable gitlab-runner

# Vérifier le statut
sudo systemctl status gitlab-runner
```

### Vérification et tests

1. Vérifiez que le runner apparaît dans l'interface GitLab (Settings > CI/CD > Runners)
2. Créez un fichier `.gitlab-ci.yml` à la racine de votre projet avec un job simple :

```yaml
test_job:
  script:
    - echo "Le runner fonctionne correctement!"
```

3. Commitez et poussez ce fichier pour déclencher un pipeline de test

### Bonnes pratiques et sécurité

- Utilisez des tags spécifiques pour cibler les runners appropriés
- Limitez l'accès au runner en utilisant des tokens de projet ou de groupe
- Mettez régulièrement à jour GitLab Runner : `sudo apt-get update && sudo apt-get upgrade gitlab-runner`
- Pour les environnements sensibles, utilisez des runners en mode autoscaling avec des instances éphémères
