## Cheatsheet Commandes Windows

### Navigation et gestion des fichiers

- **dir [options]** : Affiche le contenu d'un répertoire
    - Options : /a (fichiers cachés), /s (sous-répertoires)
- **cd [chemin]** : Change de répertoire
    - cd .. : Remonte d'un niveau
    - cd \ : Retourne à la racine
- **mkdir** ou **md [nom]** : Crée un nouveau répertoire
- **rmdir** ou **rd [nom]** : Supprime un répertoire
- **copy [source] [destination]** : Copie des fichiers
- **xcopy [source] [destination]** : Copie des fichiers et répertoires
- **move [source] [destination]** : Déplace des fichiers
- **del [fichier]** : Supprime des fichiers
- **rename** ou **ren [ancien] [nouveau]** : Renomme un fichier ou dossier
- **tree /F** : Affiche l'arborescence avec fichiers

### Système

- **systeminfo** : Affiche les informations système détaillées
- **tasklist** : Liste tous les processus en cours
- **taskkill /PID [num] /F** : Termine un processus
- **sfc /scannow** : Vérifie l'intégrité des fichiers système
- **chkdsk [lecteur:] /F** : Vérifie et répare les erreurs de disque
- **shutdown /s /t 0** : Arrête l'ordinateur immédiatement

### Réseau

- **ipconfig /all** : Affiche la configuration IP détaillée
- **ping [adresse]** : Teste la connectivité réseau
- **tracert [adresse]** : Trace l'itinéraire vers une destination
- **netstat -ano** : Affiche les connexions réseau actives avec PID
- **nslookup [domaine]** : Interroge les serveurs DNS

### Utilisateurs et sécurité

- **net user [nom] [mot_de_passe] /add** : Ajoute un utilisateur
- **net localgroup [groupe] [utilisateur] /add** : Ajoute un utilisateur à un groupe
- **gpupdate /force** : Force la mise à jour des stratégies de groupe

### Divers

- **cls** : Efface l'écran
- **help [commande]** : Affiche l'aide pour une commande
- **echo [message]** : Affiche un message
- **find "texte" [fichier]** : Recherche une chaîne dans des fichiers
- **type [fichier]** : Affiche le contenu d'un fichier texte
- **powershell** : Lance PowerShell depuis CMD

### Astuces

- Utilisez la touche Tab pour l'auto-complétion
- Utilisez les flèches haut/bas pour naviguer dans l'historique des commandes
- Utilisez **[commande] /?** pour obtenir l'aide sur une commande spécifique
- **Ctrl+C** : Interrompt une commande en cours d'exécution