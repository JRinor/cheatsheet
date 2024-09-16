## Cheatsheet Commandes Linux

### Navigation dans le système de fichiers

- **`pwd`** : Affiche le chemin du répertoire courant.

- **`ls [options] [chemin]`** : Liste le contenu d'un répertoire.
  - **Options** :
    - `-l` : Format long.
    - `-a` : Affiche les fichiers cachés.
    - `-h` : Tailles lisibles par l'homme.
    - `-R` : Récursif.

- **`cd [chemin]`** : Change le répertoire courant.
  - **Raccourcis** :
    - `cd -` : Retourne au répertoire précédent.
    - `cd ~` ou `cd` : Accède au répertoire personnel.
    - `cd /` : Accède à la racine.

### Gestion des fichiers et répertoires

- **`touch [options] <fichier>`** : Crée un fichier vide ou met à jour l'horodatage.

- **`cat [options] <fichier>`** : Affiche le contenu d'un fichier.
  - **Options** :
    - `-n` : Numérote les lignes.
    - `-A` : Affiche les caractères non imprimables.

- **`cp [options] <source> <destination>`** : Copie fichiers et répertoires.
  - **Options** :
    - `-r` ou `-R` : Récursif.
    - `-i` : Interactif.
    - `-p` : Préserve les attributs.

- **`mv [options] <source> <destination>`** : Déplace ou renomme.
  - **Options** :
    - `-i` : Interactif.
    - `-u` : Met à jour.

- **`rm [options] <fichier/répertoire>`** : Supprime fichiers ou répertoires.
  - **Options** :
    - `-r` : Récursif.
    - `-f` : Force la suppression sans confirmation.
    - `-i` : Interactif.

- **`mkdir [options] <nom_répertoire>`** : Crée un nouveau répertoire.
  - **Option** : `-p`.

- **`rmdir <nom_répertoire>`** : Supprime un répertoire vide.

### Manipulation de texte et recherche

- **`grep [options] <motif> <fichier>`** : Recherche un motif dans un fichier.
  - **Options** :
    - `-i` : Insensible à la casse.
    - `-r` : Récursif.
    - `-n` : Affiche les numéros de ligne.

- **`sed 's/ancien/nouveau/g' <fichier>`** : Remplace du texte dans un fichier.

- **`awk '{print $1}' <fichier>`** : Traitement de texte avancé.

### Gestion des processus et ressources

- **`ps [options]`** : Affiche les processus en cours.
  - **Exemple** : `ps aux`.

- **`top`** ou **`htop`** : Affiche les processus en temps réel.

- **`kill [signal] <PID>`** : Envoie un signal à un processus.

- **`free -h`** : Affiche l'utilisation de la mémoire.

- **`df -h`** : Affiche l'utilisation de l'espace disque.

### Réseau

- **`ifconfig`** ou **`ip addr`** : Affiche la configuration réseau.

- **`ping <hôte>`** : Teste la connectivité avec un hôte.

- **`netstat -tuln`** : Affiche les connexions réseau actives.

### Gestion des utilisateurs et permissions

- **`sudo <commande>`** : Exécute une commande avec des privilèges root.

- **`chmod [options] <permissions> <fichier>`** : Modifie les permissions d'un fichier.

- **`chown [options] <utilisateur>:<groupe> <fichier>`** : Change le propriétaire d'un fichier.

### Autres commandes utiles

- **`man <commande>`** : Affiche le manuel d'une commande.

- **`history`** : Affiche l'historique des commandes.

- **`tar [options] <archive> <fichiers>`** : Crée ou extrait des archives.

- **Exemple pour tar**: `tar -czvf archive.tar.gz dossier/`.

- **`find <chemin> -name "<motif>"`** : Recherche des fichiers.
  - Exemple: `find /home -name "*.txt"`.