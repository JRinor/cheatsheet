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

// Opérateurs de comparaison
db.collection.find({champ1: {$gt: 50}})  // Plus grand que (>)
db.collection.find({champ1: {$gte: 50}}) // Plus grand ou égal (>=)
db.collection.find({champ1: {$lt: 50}})  // Plus petit que (<)
db.collection.find({champ1: {$lte: 50}}) // Plus petit ou égal (<=)
db.collection.find({champ1: {$ne: "valeur1"}}) // Différent de (!=)
db.collection.find({champ1: {$in: ["valeur1", "valeur2"]}}) // Dans la liste
db.collection.find({champ1: {$nin: ["valeur1", "valeur2"]}}) // Pas dans la liste

// Opérateurs logiques
db.collection.find({$and: [{champ1: "valeur1"}, {champ2: "valeur2"}]})
db.collection.find({$or: [{champ1: "valeur1"}, {champ2: "valeur2"}]})
db.collection.find({champ1: {$not: {$eq: "valeur1"}}})

// Existence d'un champ
db.collection.find({champ1: {$exists: true}})

// Expressions régulières
db.collection.find({champ1: /^valeur/}) // Commence par "valeur"

// Projection (sélection des champs)
db.collection.find({}, {champ1: 1, champ2: 1, _id: 0})

// Limiter les résultats
db.collection.find().limit(5)

// Trier les résultats
db.collection.find().sort({champ1: 1}) // 1 pour ascendant, -1 pour descendant

// Sauter des résultats (pour la pagination)
db.collection.find().skip(10).limit(5)
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

// Incrémenter une valeur
db.collection.updateOne({champ1: "valeur1"}, {$inc: {compteur: 1}})

// Ajouter à un tableau
db.collection.updateOne({champ1: "valeur1"}, {$push: {tableau: "nouvel_element"}})

// Supprimer d'un tableau
db.collection.updateOne({champ1: "valeur1"}, {$pull: {tableau: "element_a_supprimer"}})
```

### Suppression (Delete)

```javascript
// Supprimer un document
db.collection.deleteOne({champ1: "valeur1"})

// Supprimer plusieurs documents
db.collection.deleteMany({champ1: "valeur1"})
```

## Agrégations

```javascript
// Pipeline d'agrégation
db.collection.aggregate([
  {$match: {champ1: "valeur1"}},
  {$group: {_id: "$champ2", total: {$sum: 1}}},
  {$sort: {total: -1}},
  {$limit: 5}
])

// Opérateurs d'agrégation courants
$sum, $avg, $min, $max, $first, $last, $push
```

## Indexation

```javascript
// Créer un index
db.collection.createIndex({champ1: 1})

// Créer un index composé
db.collection.createIndex({champ1: 1, champ2: -1})

// Créer un index unique
db.collection.createIndex({champ1: 1}, {unique: true})

// Créer un index TTL (Time-To-Live)
db.collection.createIndex({dateExpiration: 1}, {expireAfterSeconds: 3600})

// Lister les index
db.collection.getIndexes()

// Supprimer un index
db.collection.dropIndex("nom_index")
```

Ce cheat sheet étendu couvre davantage d'opérations et d'opérateurs MongoDB, y compris les comparaisons avancées, les opérateurs logiques, les expressions régulières, et plus encore. Il devrait vous fournir une référence plus complète pour vos travaux avec MongoDB.