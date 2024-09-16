## Cheatsheet Commandes Linux

### Navigation dans le système de fichiers

- **`pwd`** : Affiche le chemin du répertoire courant.
  
- **`ls`** : Liste le contenu du répertoire courant.
  - **Options** :
    - `ls -l` : Affiche les détails des fichiers (permissions, taille, date).
    - `ls -a` : Affiche tous les fichiers, y compris ceux cachés.
    - `ls -la` : Combine les deux options ci-dessus.

- **`cd <répertoire>`** : Change le répertoire courant vers `<répertoire>`.
  - **Exemples** :
    - `cd ..` : Remonte d'un niveau dans l'arborescence.
    - `cd ~` : Accède au répertoire personnel de l'utilisateur.

### Gestion des fichiers

- **`touch <nom_fichier>`** : Crée un fichier vide nommé `<nom_fichier>`.

- **`cat <nom_fichier>`** : Affiche le contenu du fichier `<nom_fichier>`.

- **`cp <source> <destination>`** : Copie un fichier ou un répertoire.
  - **Options** :
    - `cp -r <source> <destination>` : Copie un répertoire et son contenu.

- **`mv <source> <destination>`** : Déplace ou renomme un fichier ou un répertoire.

- **`rm <nom_fichier>`** : Supprime le fichier `<nom_fichier>`.
  - **Options** :
    - `rm -r <nom_répertoire>` : Supprime un répertoire et son contenu.
    - `rm -f <nom_fichier>` : Force la suppression sans demander confirmation.

### Gestion des répertoires

- **`mkdir <nom_répertoire>`** : Crée un nouveau répertoire nommé `<nom_répertoire>`.

- **`rmdir <nom_répertoire>`** : Supprime un répertoire vide nommé `<nom_répertoire>`.

### Informations système

- **`free -h`** : Affiche la mémoire utilisée et disponible (en format lisible).

- **`df -h`** : Affiche l'espace disque utilisé et disponible sur les systèmes de fichiers montés.

- **`top`** : Affiche les processus en cours et leur utilisation des ressources en temps réel.

### Autres commandes utiles

- **`man <commande>`** : Ouvre le manuel de la commande spécifiée pour plus d'informations.

- **`sudo <commande>`** : Exécute une commande avec des privilèges administratifs.

- **`history`** : Affiche l'historique des commandes précédemment exécutées.

- **`grep <motif> <fichier>`** : Recherche le motif spécifié dans le fichier donné.
