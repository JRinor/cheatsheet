## Cheatsheet Git

### Initialisation et clonage

- **`git init`** : Initialise un nouveau dépôt Git dans le répertoire courant.

- **`git clone <url>`** : Clone un dépôt distant sur votre machine locale.
  - Exemple : `git clone https://github.com/user/repo.git`

### Gestion des modifications

- **`git add <fichier>`** : Ajoute un fichier à la zone de staging.
  - `git add .` : Ajoute tous les fichiers modifiés.
  - `git add -p` : Ajoute interactivement des parties de fichiers.

- **`git commit -m "message"`** : Crée un nouveau commit avec les fichiers stagés.
  - `git commit -am "message"` : Ajoute tous les fichiers modifiés et crée un commit.

- **`git status`** : Affiche l'état actuel du dépôt.

- **`git diff`** : Affiche les différences entre les fichiers modifiés et la dernière version commitée.
  - `git diff --staged` : Affiche les différences pour les fichiers stagés.

### Branches et fusion

- **`git branch`** : Liste toutes les branches locales.
  - `git branch <nom>` : Crée une nouvelle branche.
  - `git branch -d <nom>` : Supprime une branche.

- **`git checkout <branche>`** : Bascule sur la branche spécifiée.
  - `git checkout -b <nouvelle-branche>` : Crée une nouvelle branche et bascule dessus.

- **`git merge <branche>`** : Fusionne la branche spécifiée dans la branche courante.

- **`git rebase <branche>`** : Réapplique les commits de la branche courante sur une autre branche.

### Interaction avec le dépôt distant

- **`git pull`** : Récupère et fusionne les modifications du dépôt distant.

- **`git push`** : Envoie les commits locaux vers le dépôt distant.
  - `git push -u origin <branche>` : Pousse une nouvelle branche vers le dépôt distant.

- **`git fetch`** : Récupère les modifications du dépôt distant sans les fusionner.

- **`git remote -v`** : Affiche les dépôts distants liés au dépôt local.

### Historique et logs

- **`git log`** : Affiche l'historique des commits.
  - `git log --oneline` : Affiche un résumé compact de l'historique.
  - `git log --graph` : Affiche l'historique sous forme de graphe.

### Annulation et modification

- **`git reset <fichier>`** : Retire un fichier de la zone de staging.
  - `git reset --hard HEAD` : Annule toutes les modifications locales non commitées.

- **`git revert <commit>`** : Crée un nouveau commit qui annule les changements d'un commit spécifique.

- **`git stash`** : Met de côté les modifications en cours.
  - `git stash pop` : Réapplique les modifications mises de côté.

### Configuration

- **`git config --global user.name "Nom"`** : Configure le nom d'utilisateur Git global.
- **`git config --global user.email "email@example.com"`** : Configure l'email Git global.

### Astuces avancées

- **`git cherry-pick <commit>`** : Applique les changements d'un commit spécifique à la branche courante.
- **`git bisect`** : Aide à trouver le commit qui a introduit un bug.
- **`git blame <fichier>`** : Montre qui a modifié chaque ligne d'un fichier et quand.