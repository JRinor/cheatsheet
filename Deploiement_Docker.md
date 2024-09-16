## Cheatsheet Docker pour le déploiement de code

### Création et gestion des images

- **Construire une image** :
  `docker build -t nom_image:tag -f Dockerfile .`
  - `-t` : Tag de l'image
  - `-f` : Spécifie le Dockerfile à utiliser

- **Lister les images** :
  `docker images [options]`
  - `--format "{{.ID}}: {{.Repository}}"` : Personnalise l'affichage

- **Supprimer une image** :
  `docker rmi nom_image:tag`

### Gestion des conteneurs

- **Lancer un conteneur** :
  `docker run [options] nom_image:tag [commande]`
  - `-d` : Mode détaché
  - `--name nom_conteneur` : Nomme le conteneur
  - `-p port_hôte:port_conteneur` : Mappe les ports
  - `-e CLE=VALEUR` : Définit des variables d'environnement

- **Lister les conteneurs** :
  `docker ps [options]`
  - `-a` : Affiche tous les conteneurs (y compris ceux arrêtés)

- **Arrêter un conteneur** :
  `docker stop nom_conteneur`

- **Supprimer un conteneur** :
  `docker rm [options] nom_conteneur`
  - `-f` : Force la suppression d'un conteneur en cours d'exécution

### Déploiement et registres

- **Se connecter à un registre** :
  `docker login [options] [serveur]`

- **Pousser une image vers un registre** :
  `docker push nom_registre/nom_image:tag`

- **Tirer une image depuis un registre** :
  `docker pull nom_registre/nom_image:tag`

### Gestion des volumes

- **Créer un volume** :
  `docker volume create [options] nom_volume`

- **Lister les volumes** :
  `docker volume ls`

- **Monter un volume** :
  `docker run -v nom_volume:/chemin/dans/conteneur nom_image:tag`

### Réseau

- **Créer un réseau** :
  `docker network create [options] nom_réseau`

- **Lister les réseaux** :
  `docker network ls`

- **Connecter un conteneur à un réseau** :
  `docker network connect nom_réseau nom_conteneur`

### Logs et debugging

- **Voir les logs d'un conteneur** :
  `docker logs [options] nom_conteneur`
  - `-f` : Suit les logs en temps réel
  - `--tail n` : Affiche les n dernières lignes

- **Exécuter une commande dans un conteneur** :
  `docker exec [options] nom_conteneur commande`
  - `-it` : Mode interactif avec un terminal

### Mise à jour et redéploiement

- **Mettre à jour un conteneur** :
  ```
  docker pull nom_image:nouveau_tag
  docker stop nom_conteneur
  docker rm nom_conteneur
  docker run [options] nom_image:nouveau_tag
  ```

### Commandes utiles

- **Nettoyer les ressources inutilisées** :
  `docker system prune [options]`
  - `-a` : Supprime également les images non utilisées

- **Inspecter un objet Docker** :
  `docker inspect [options] objet`

- **Voir l'utilisation des ressources** :
  `docker stats [options]`

### Docker Compose

- **Lancer des services définis dans docker-compose.yml** :
  `docker-compose up [options]`
  - `-d` : Mode détaché

- **Arrêter les services** :
  `docker-compose down [options]`
  - `--volumes` : Supprime également les volumes
