## Cheatsheet Docker

### Concepts de base
- **"image" Docker** = Modèle permettant de créer un conteneur.
- **"conteneur" Docker** = Une version exécutée de l'image.

### Commandes Docker
- **`docker pull ubuntu`** = Télécharge l'image Ubuntu depuis le Docker Hub.

- **`docker run`** = Combine `docker pull` et `docker start`.  
  - **Exemples :**
    - `docker run -it --name ubuntu1 ubuntu` = Crée et démarre un conteneur nommé "ubuntu1" en mode interactif.
    - `docker run -it --name apache1 -p 5000:80` = Crée et démarre un conteneur nommé "apache1" en mode interactif, redirigeant le port 5000 de l'hôte vers le port 80 du conteneur.

- **`docker ps -a`** = Affiche tous les conteneurs, qu'ils soient en cours d'exécution ou arrêtés.

- **`docker ps`** = Affiche uniquement les conteneurs en cours d'exécution.

- **`docker start ubuntu1`** = Démarre le conteneur nommé "ubuntu1".

- **`docker stop <nom ou id>`** = Stoppe le conteneur spécifié.

- **`docker attach ubuntu1`** = Se connecte au terminal du conteneur "ubuntu1".

- **`docker exec <nom ou id> <commande>`** = Lance une commande dans le conteneur spécifié.

- **`docker rm <nom ou id>`** = Supprime un conteneur spécifié.

- **`docker image rm <nom ou id>`** = Supprime une image spécifiée.

- **`docker images`** = Liste toutes les images Docker disponibles localement.

- **`docker build -t <nom_image>:<tag> .`** = Crée une image à partir d'un Dockerfile dans le répertoire courant.

- **`docker logs <nom ou id>`** = Affiche les logs du conteneur spécifié.

- **`docker volume ls`** = Liste tous les volumes Docker disponibles.

- **`docker network ls`** = Liste tous les réseaux Docker disponibles.

- **`docker inspect <nom ou id>`** = Obtient des informations détaillées sur un conteneur ou une image.

- **`docker commit <conteneur> <nouvelle_image>`** = Crée une nouvelle image à partir d'un conteneur modifié.

- **`docker push <nom_image>`** = Envoie une image vers un registre Docker distant (comme Docker Hub).
