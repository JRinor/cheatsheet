## Cheat Sheet MongoDB Avancé

### Opérations CRUD

#### Création (Create)

```javascript
// Insérer un document
db.collection.insertOne({champ1: "valeur1", champ2: "valeur2"})

// Insérer plusieurs documents
db.collection.insertMany([
  {champ1: "valeur1", champ2: "valeur2"},
  {champ1: "valeur3", champ2: "valeur4"}
])

// Insérer avec options
db.collection.insertOne({champ1: "valeur1"}, {writeConcern: {w: "majority", wtimeout: 5000}})
```

#### Lecture (Read)

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
db.collection.find({$nor: [{champ1: "valeur1"}, {champ2: "valeur2"}]})

// Existence d'un champ
db.collection.find({champ1: {$exists: true}})

// Expressions régulières
db.collection.find({champ1: /^valeur/}) // Commence par "valeur"
db.collection.find({champ1: /valeur$/i}) // Termine par "valeur", insensible à la casse

// Projection (sélection des champs)
db.collection.find({}, {champ1: 1, champ2: 1, _id: 0})

// Limiter les résultats
db.collection.find().limit(5)

// Trier les résultats
db.collection.find().sort({champ1: 1, champ2: -1}) // 1 pour ascendant, -1 pour descendant

// Pagination
db.collection.find().skip(10).limit(5)

// Comptage
db.collection.countDocuments({champ1: "valeur1"})

// Distinct
db.collection.distinct("champ1")
```

#### Mise à jour (Update)

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

// Opérations sur les tableaux
db.collection.updateOne({champ1: "valeur1"}, {$push: {tableau: "nouvel_element"}})
db.collection.updateOne({champ1: "valeur1"}, {$pull: {tableau: "element_a_supprimer"}})
db.collection.updateOne({champ1: "valeur1"}, {$addToSet: {tableau: "element_unique"}})

// Opérateurs de mise à jour avancés
db.collection.updateOne({champ1: "valeur1"}, {$mul: {champ2: 2}}) // Multiplier
db.collection.updateOne({champ1: "valeur1"}, {$rename: {"ancien_nom": "nouveau_nom"}}) // Renommer un champ
db.collection.updateOne({champ1: "valeur1"}, {$unset: {champ2: ""}}) // Supprimer un champ

// Upsert (insérer si n'existe pas, sinon mettre à jour)
db.collection.updateOne({champ1: "valeur1"}, {$set: {champ2: "valeur2"}}, {upsert: true})
```

#### Suppression (Delete)

```javascript
// Supprimer un document
db.collection.deleteOne({champ1: "valeur1"})

// Supprimer plusieurs documents
db.collection.deleteMany({champ1: "valeur1"})

// Supprimer tous les documents
db.collection.deleteMany({})
```

### Agrégations

```javascript
// Pipeline d'agrégation
db.collection.aggregate([
  {$match: {champ1: "valeur1"}},
  {$group: {_id: "$champ2", total: {$sum: 1}}},
  {$sort: {total: -1}},
  {$limit: 5}
])

// Opérateurs d'agrégation courants
$sum, $avg, $min, $max, $first, $last, $push, $addToSet

// Exemple d'agrégation avancée
db.collection.aggregate([
  {$match: {date: {$gte: new Date("2024-01-01")}}},
  {$group: {
    _id: {mois: {$month: "$date"}, annee: {$year: "$date"}},
    total: {$sum: "$montant"},
    moyenne: {$avg: "$montant"},
    count: {$sum: 1}
  }},
  {$sort: {"_id.annee": 1, "_id.mois": 1}},
  {$project: {
    _id: 0,
    mois: "$_id.mois",
    annee: "$_id.annee",
    total: 1,
    moyenne: {$round: ["$moyenne", 2]},
    count: 1
  }}
])
```

### Indexation

```javascript
// Créer un index
db.collection.createIndex({champ1: 1})

// Créer un index composé
db.collection.createIndex({champ1: 1, champ2: -1})

// Créer un index unique
db.collection.createIndex({champ1: 1}, {unique: true})

// Créer un index TTL (Time-To-Live)
db.collection.createIndex({dateExpiration: 1}, {expireAfterSeconds: 3600})

// Créer un index de texte
db.collection.createIndex({description: "text"})

// Lister les index
db.collection.getIndexes()

// Supprimer un index
db.collection.dropIndex("nom_index")

// Supprimer tous les index (sauf _id)
db.collection.dropIndexes()
```

### Opérations avancées

```javascript
// Transactions
session = db.getMongo().startSession()
session.startTransaction()
try {
  db.collection1.insertOne({...})
  db.collection2.updateOne({...})
  session.commitTransaction()
} catch (error) {
  session.abortTransaction()
} finally {
  session.endSession()
}

// Recherche de texte
db.collection.find({$text: {$search: "phrase à rechercher"}})

// Géospatial
db.collection.createIndex({location: "2dsphere"})
db.collection.find({
  location: {
    $near: {
      $geometry: {
        type: "Point",
        coordinates: [longitude, latitude]
      },
      $maxDistance: 1000 // en mètres
    }
  }
})

// Explain pour l'analyse des performances
db.collection.find({champ1: "valeur1"}).explain("executionStats")
```

Ce cheat sheet amélioré couvre un large éventail d'opérations MongoDB, des basiques aux plus avancées. Il inclut des exemples pour les transactions, la recherche de texte, les opérations géospatiales et l'analyse des performances, qui sont des concepts importants pour un étudiant en informatique. N'hésitez pas à l'utiliser comme référence rapide pour vos travaux d'études et vos projets.