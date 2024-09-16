## Cheatsheet Docker pour le déploiement de code

### Création de l'image

- **Construire l'image** :
  `docker build -t nom_image:tag .`

- **Lister les images** :
  `docker images`

### Gestion des conteneurs

- **Lancer un conteneur** :
  `docker run -d --name nom_conteneur -p port_hôte:port_conteneur nom_image:tag`

- **Lister les conteneurs en cours d'exécution** :
  `docker ps`

- **Arrêter un conteneur** :
  `docker stop nom_conteneur`

- **Supprimer un conteneur** :
  `docker rm nom_conteneur`

### Déploiement

- **Pousser l'image vers un registre** :
  `docker push nom_registre/nom_image:tag`

- **Tirer l'image depuis un registre** :
  `docker pull nom_registre/nom_image:tag`

- **Exécuter un conteneur depuis une image distante** :
  `docker run -d --name nom_conteneur -p port_hôte:port_conteneur nom_registre/nom_image:tag`

### Gestion des volumes

- **Créer un volume** :
  `docker volume create nom_volume`

- **Monter un volume** :
  `docker run -v nom_volume:/chemin/dans/conteneur nom_image:tag`

### Réseau

- **Créer un réseau** :
  `docker network create nom_réseau`

- **Connecter un conteneur à un réseau** :
  `docker network connect nom_réseau nom_conteneur`

### Logs et debugging

- **Voir les logs d'un conteneur** :
  `docker logs nom_conteneur`

- **Exécuter une commande dans un conteneur en cours d'exécution** :
  `docker exec -it nom_conteneur commande`

### Mise à jour et redéploiement

- **Mettre à jour l'image** :
  `docker build -t nom_image:nouveau_tag .`

- **Arrêter l'ancien conteneur** :
  `docker stop nom_ancien_conteneur`

- **Lancer le nouveau conteneur** :
  `docker run -d --name nom_nouveau_conteneur -p port_hôte:port_conteneur nom_image:nouveau_tag`

### Commandes utiles

- **Nettoyer les ressources inutilisées** :
  `docker system prune`

- **Inspecter un conteneur** :
  `docker inspect nom_conteneur`
