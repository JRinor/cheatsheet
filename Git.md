- **`git init`** = Initialise un nouveau repository Git dans le dossier courant.

- **`git clone <url>`** = Copie un repository distant sur votre machine locale.

- **`git add <fichier>`** = Ajoute un fichier à la zone de staging.
  - **Exemple :** `git add .` = Ajoute tous les fichiers modifiés à la zone de staging.

- **`git commit -m "message"`** = Crée un nouveau commit avec les fichiers de la zone de staging.

- **`git status`** = Affiche l'état actuel du repository (fichiers modifiés, ajoutés, supprimés).

- **`git log`** = Affiche l'historique des commits.

- **`git branch`** = Liste toutes les branches locales.
  - **`git branch <nom>`** = Crée une nouvelle branche.

- **`git checkout <branche>`** = Bascule sur la branche spécifiée.
  - **`git checkout -b <nouvelle-branche>`** = Crée une nouvelle branche et bascule dessus.

- **`git merge <branche>`** = Fusionne la branche spécifiée dans la branche courante.

- **`git pull`** = Récupère les modifications du repository distant et les fusionne dans la branche courante.

- **`git push`** = Envoie les commits locaux vers le repository distant.
  - **`git push -u origin <branche>`** = Pousse une nouvelle branche vers le repository distant.

- **`git fetch`** = Récupère les modifications du repository distant sans les fusionner.

- **`git diff`** = Affiche les différences entre les fichiers modifiés et la dernière version commitée.

- **`git reset <fichier>`** = Retire un fichier de la zone de staging.
  - **`git reset --hard HEAD`** = Annule toutes les modifications locales non commitées.

- **`git stash`** = Met de côté les modifications en cours pour travailler sur autre chose.
  - **`git stash pop`** = Réapplique les modifications mises de côté.

- **`git remote -v`** = Affiche les repositories distants liés au repository local.

- **`git config --global user.name "Nom"`** = Configure le nom d'utilisateur Git global.
  - **`git config --global user.email "email@example.com"`** = Configure l'email Git global.
