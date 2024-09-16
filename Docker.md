## Cheatsheet Docker

### Concepts de base
- **Image Docker** : Modèle en lecture seule pour créer des conteneurs.
- **Conteneur Docker** : Instance exécutable d'une image.
- **Dockerfile** : Script de configuration pour construire une image.
- **Docker Hub** : Registre public d'images Docker.

### Gestion des images
- **`docker pull <image>:<tag>`** : Télécharge une image depuis un registre.
  - Exemple : `docker pull ubuntu:22.04`

- **`docker images`** : Liste les images locales.

- **`docker image rm <image>`** ou **`docker rmi <image>`** : Supprime une image.

- **`docker build -t <nom>:<tag> .`** : Construit une image à partir d'un Dockerfile.
  - Option `-f <fichier>` : Spécifie un Dockerfile alternatif.

- **`docker commit <conteneur> <nouvelle_image>`** : Crée une image à partir d'un conteneur modifié.

### Gestion des conteneurs
- **`docker run [options] <image> [commande]`** : Crée et démarre un nouveau conteneur.
  - Options courantes :
    - `-d` : Mode détaché (background).
    - `-it` : Mode interactif avec un terminal.
    - `--name <nom>` : Attribue un nom au conteneur.
    - `-p <hôte>:<conteneur>` : Mappe les ports.
    - `-v <hôte>:<conteneur>` : Monte un volume.

- **`docker ps`** : Liste les conteneurs en cours d'exécution.
  - Option `-a` : Inclut les conteneurs arrêtés.

- **`docker start <conteneur>`** : Démarre un conteneur arrêté.

- **`docker stop <conteneur>`** : Arrête un conteneur en cours d'exécution.

- **`docker restart <conteneur>`** : Redémarre un conteneur.

- **`docker rm <conteneur>`** : Supprime un conteneur arrêté.
  - Option `-f` : Force la suppression d'un conteneur en cours d'exécution.

- **`docker exec -it <conteneur> <commande>`** : Exécute une commande dans un conteneur en cours d'exécution.

### Logs et debugging
- **`docker logs <conteneur>`** : Affiche les logs d'un conteneur.
  - Option `-f` : Suit les logs en temps réel.

- **`docker inspect <conteneur/image>`** : Affiche des informations détaillées.

### Réseau
- **`docker network ls`** : Liste les réseaux Docker.

- **`docker network create <nom>`** : Crée un nouveau réseau.

- **`docker network connect <réseau> <conteneur>`** : Connecte un conteneur à un réseau.

### Volumes
- **`docker volume ls`** : Liste les volumes.

- **`docker volume create <nom>`** : Crée un nouveau volume.

- **`docker volume rm <nom>`** : Supprime un volume.

### Docker Compose
- **`docker-compose up`** : Démarre les services définis dans docker-compose.yml.
  - Option `-d` : Mode détaché.

- **`docker-compose down`** : Arrête et supprime les conteneurs, réseaux, et volumes définis.

### Nettoyage
- **`docker system prune`** : Supprime tous les conteneurs, réseaux, et images inutilisés.
  - Option `-a` : Inclut les images non taguées.