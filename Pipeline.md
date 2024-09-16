## Cheatsheet GitHub Actions Pipeline

### Structure de base
```yaml
name: Mon Pipeline CI/CD

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

env:
  GLOBAL_VAR: valeur

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Étape de build
        run: echo "Build du projet"
```

### Événements déclencheurs courants
- `push`: Déclenché lors d'un push
- `pull_request`: Déclenché lors d'une pull request
- `schedule: - cron: '0 0 * * *'`: Déclenché selon un planning (quotidien à minuit)
- `workflow_dispatch`: Déclenché manuellement
- `release: types: [created]`: Déclenché lors de la création d'une release

### Environnements d'exécution
- `runs-on: ubuntu-latest`
- `runs-on: windows-latest`
- `runs-on: macos-latest`
- `runs-on: self-hosted`: Pour les runners auto-hébergés

### Actions courantes
- `actions/checkout@v3`: Récupère le code du repository
- `actions/setup-node@v3`: Configure Node.js
- `actions/cache@v3`: Met en cache des dépendances
- `actions/upload-artifact@v3`: Téléverse des artefacts
- `actions/download-artifact@v3`: Télécharge des artefacts

### Variables et secrets
- Variables d'environnement : `${{ env.MA_VARIABLE }}`
- Secrets : `${{ secrets.MON_SECRET }}`
- Variables de contexte : `${{ github.repository }}`

### Commandes shell
```yaml
- name: Exécuter des commandes shell
  run: |
    echo "Première commande"
    echo "Deuxième commande"
  shell: bash
```

### Conditions et expressions
```yaml
- name: Étape conditionnelle
  if: ${{ github.event_name == 'push' && github.ref == 'refs/heads/main' }}
  run: echo "Exécuté uniquement lors d'un push sur main"
```

### Matrices
```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest]
    node-version: [14.x, 16.x, 18.x]
steps:
  - uses: actions/setup-node@v3
    with:
      node-version: ${{ matrix.node-version }}
```

### Gestion des artefacts
```yaml
- uses: actions/upload-artifact@v3
  with:
    name: mon-artefact
    path: dist/
- uses: actions/download-artifact@v3
  with:
    name: mon-artefact
```

### Dépendances entre jobs
```yaml
jobs:
  job1:
    # ...
  job2:
    needs: job1
    # ...
```

### Utilisation de conteneurs
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    container: node:14
```

### Parallélisation
```yaml
jobs:
  test:
    strategy:
      max-parallel: 2
      matrix:
        test-group: [1, 2, 3, 4]
```

### Timeouts
```yaml
jobs:
  job1:
    timeout-minutes: 30
```

### Utilisation de services
```yaml
jobs:
  test:
    services:
      redis:
        image: redis
        ports:
          - 6379:6379
```