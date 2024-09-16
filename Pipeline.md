# Cheatsheet GitHub Actions Pipeline

### Structure de base
```yaml
name: Mon Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Étape de build
        run: echo "Build du projet"
```

### Événements déclencheurs courants
- `push`: Déclenché lors d'un push
- `pull_request`: Déclenché lors d'une pull request
- `schedule`: Déclenché selon un planning (cron)
- `workflow_dispatch`: Déclenché manuellement

### Environnements d'exécution
- `runs-on: ubuntu-latest`
- `runs-on: windows-latest`
- `runs-on: macos-latest`

### Actions courantes
- `actions/checkout@v2`: Récupère le code du repository
- `actions/setup-node@v2`: Configure Node.js
- `actions/cache@v2`: Met en cache des dépendances

### Variables et secrets
- Utilisation de variables : `${{ env.MA_VARIABLE }}`
- Utilisation de secrets : `${{ secrets.MON_SECRET }}`

### Commandes shell
```yaml
- name: Exécuter des commandes shell
  run: |
    echo "Première commande"
    echo "Deuxième commande"
```

### Conditions
```yaml
- name: Étape conditionnelle
  if: github.event_name == 'push'
  run: echo "Exécuté uniquement lors d'un push"
```

### Matrices
```yaml
strategy:
  matrix:
    node-version: [10.x, 12.x, 14.x]
steps:
  - uses: actions/setup-node@v2
    with:
      node-version: ${{ matrix.node-version }}
```

### Artefacts
```yaml
- uses: actions/upload-artifact@v2
  with:
    name: mon-artefact
    path: chemin/vers/artefact
```

### Dépendances entre jobs
```yaml
jobs:
  job1:
  job2:
    needs: job1
```
