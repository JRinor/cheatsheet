## Installation d'un runner GitLab en local

### Prérequis

- Un système Linux (Ubuntu/Debian recommandé)
- Accès root ou sudo
- Docker installé (optionnel mais recommandé)

### Étapes d'installation

1. **Téléchargement du binaire GitLab Runner**

```bash
sudo curl -L --output /usr/local/bin/gitlab-runner "https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64"
```

2. **Attribution des permissions d'exécution**

```bash
sudo chmod +x /usr/local/bin/gitlab-runner
```

3. **Création d'un utilisateur dédié**

```bash
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash
```

4. **Installation et démarrage du service**

```bash
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start
```

### Enregistrement du runner

1. **Récupération du token**
   - Allez dans les paramètres CI/CD de votre projet GitLab
   - Notez le token d'enregistrement du runner

2. **Lancement de l'enregistrement**

```bash
sudo gitlab-runner register
```

3. **Répondez aux questions**
   - URL de l'instance GitLab
   - Token d'enregistrement
   - Description du runner
   - Tags (optionnels)
   - Executor (choisissez 'docker' si disponible)

### Configuration (optionnelle)

Éditez le fichier de configuration pour des réglages avancés :

```bash
sudo nano /etc/gitlab-runner/config.toml
```

### Vérification

1. Vérifiez que le runner apparaît dans l'interface GitLab
2. Lancez un pipeline de test pour confirmer le bon fonctionnement

### Bonnes pratiques

- Utilisez des tags pour cibler des runners spécifiques
- Limitez l'accès au runner pour des raisons de sécurité
- Mettez régulièrement à jour le runner
