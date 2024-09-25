## Opérations CRUD

### Création (Create)

```javascript
// Insérer un document
db.collection.insertOne({champ1: "valeur1", champ2: "valeur2"})

// Insérer plusieurs documents
db.collection.insertMany([
  {champ1: "valeur1", champ2: "valeur2"},
  {champ1: "valeur3", champ2: "valeur4"}
])
```

### Lecture (Read)

```javascript
// Trouver tous les documents
db.collection.find()

// Trouver avec des critères
db.collection.find({champ1: "valeur1"})

// Limiter les résultats
db.collection.find().limit(5)

// Trier les résultats
db.collection.find().sort({champ1: 1}) // 1 pour ascendant, -1 pour descendant
```

### Mise à jour (Update)

```javascript
// Mettre à jour un document
db.collection.updateOne(
  {champ1: "valeur1"}, 
  {$set: {champ2: "nouvelle_valeur"}}
)

// Mettre à jour plusieurs documents
db.collection.updateMany(
  {champ1: "valeur1"}, 
  {$set: {champ2: "nouvelle_valeur"}}
)
```

### Suppression (Delete)

```javascript
// Supprimer un document
db.collection.deleteOne({champ1: "valeur1"})

// Supprimer plusieurs documents
db.collection.deleteMany({champ1: "valeur1"})
```

## Opérations sur les collections

```javascript
// Créer une collection
db.createCollection("nom_collection")

// Lister les collections
show collections

// Supprimer une collection
db.nom_collection.drop()
```

## Opérations sur les bases de données

```javascript
// Afficher la base de données actuelle
db

// Changer de base de données
use nom_base_de_donnees

// Lister les bases de données
show dbs

// Supprimer la base de données actuelle
db.dropDatabase()
```

## Agrégations

```javascript
// Pipeline d'agrégation simple
db.collection.aggregate([
  {$match: {champ1: "valeur1"}},
  {$group: {_id: "$champ2", total: {$sum: 1}}}
])
```

## Indexation

```javascript
// Créer un index
db.collection.createIndex({champ1: 1})

// Lister les index
db.collection.getIndexes()

// Supprimer un index
db.collection.dropIndex("nom_index")
```

Ce cheat sheet couvre les opérations les plus courantes dans MongoDB. N'oubliez pas que MongoDB offre de nombreuses autres fonctionnalités avancées pour des cas d'utilisation spécifiques.
