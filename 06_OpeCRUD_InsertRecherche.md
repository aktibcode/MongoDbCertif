# Chapitre : OPERATION CRUD MONGODB - INSERT ET RECHERCHE DE DOCUMENTS


# Insertion de documents dans une collection MongoDB

Regardez la vidéo ci-dessous :

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/YhMU_N5la-I"></iframe>

Examinez le code suivant, qui montre comment insérer un seul document et plusieurs documents dans une collection.

## Insérer un seul document

Permet `insertOne()`d'insérer un document dans une collection. Entre les parenthèses de insertOne(), incluez un objet qui contient les données du document. Voici un exemple :

```
db.grades.insertOne({
  student_id: 654321,
  products: [
    {
      type: "exam",
      score: 90,
    },
    {
      type: "homework",
      score: 59,
    },
    {
      type: "quiz",
      score: 75,
    },
    {
      type: "homework",
      score: 88,
    },
  ],
  class_id: 550,
})
```

## Insérer plusieurs documents

Permet `insertMany()`d'insérer plusieurs documents à la fois. Dans insertMany(), incluez les documents dans un tableau. Chaque document doit être séparé par une virgule. Voici un exemple :

```
db.grades.insertMany([
  {
    student_id: 546789,
    products: [
      {
        type: "quiz",
        score: 50,
      },
      {
        type: "homework",
        score: 70,
      },
      {
        type: "quiz",
        score: 66,
      },
      {
        type: "exam",
        score: 70,
      },
    ],
    class_id: 551,
  },
  {
    student_id: 777777,
    products: [
      {
        type: "exam",
        score: 83,
      },
      {
        type: "quiz",
        score: 59,
      },
      {
        type: "quiz",
        score: 72,
      },
      {
        type: "quiz",
        score: 67,
      },
    ],
    class_id: 550,
  },
  {
    student_id: 223344,
    products: [
      {
        type: "exam",
        score: 45,
      },
      {
        type: "homework",
        score: 39,
      },
      {
        type: "quiz",
        score: 40,
      },
      {
        type: "homework",
        score: 88,
      },
    ],
    class_id: 551,
  },
])
```

# Recherche d'un document dans une collection mongoDB

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/7bslez4sc4M"></iframe>

## Recherche de documents dans une collection MongoDB

Examinez le code suivant, qui montre comment interroger des documents dans MongoDB.

## Trouver un document avec égalité

Lorsque l'égalité avec un `_id`champ est donnée, la `find()`commande renvoie le document spécifié qui correspond à _id. Voici un exemple :

```
db.zips.find({ _id: ObjectId("5c8eccc1caa187d17ca6ed16") })
```

## Rechercher un document à l'aide de l' `$in`opérateur

Utilisez l' `$in`opérateur pour sélectionner les documents dans lesquels la valeur d'un champ est égale à n'importe quelle valeur du tableau spécifié. Voici un exemple :

```
db.zips.find({ city: { $in: ["PHOENIX", "CHICAGO"] } })
```

# Recherche de documents à l'aide d'opérateurs de comparaison

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/8JIk6RFacT4"></iframe>

## Recherche de documents à l'aide d'opérateurs de comparaison

Passez en revue les opérateurs de comparaison suivants : `$gt, $lt, $lte,`et `$gte`.

## $gt

Utilisez l'opérateur $gt pour faire correspondre les documents avec un champ supérieur à la valeur donnée. Par exemple :

```
db.sales.find({ "items.price": { $gt: 50}})
```

## $lt

Utilisez l'opérateur $lt pour faire correspondre les documents avec un champ inférieur à la valeur donnée. Par exemple :

```
db.sales.find({ "items.price": { $lt: 50}})
```

## $lte

Utilisez l'opérateur $lte pour faire correspondre les documents avec un champ inférieur ou égal à la valeur donnée. Par exemple :

```
db.sales.find({ "customer.age": { $lte: 65}})
```

## $gte

Utilisez l'opérateur $gte pour faire correspondre les documents avec un champ supérieur ou égal à la valeur donnée. Par exemple :

```
db.sales.find({ "customer.age": { $gte: 65}})
```

# Interrogation sur les éléments de tableau dans MongoDB

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/l51l9v5u2tA"></iframe>

## Interrogation sur les éléments de tableau dans MongoDB

Examinez le code suivant, qui montre comment interroger des éléments de tableau dans MongoDB.

## Rechercher des documents avec un tableau contenant une valeur spécifiée

Dans l'exemple suivant, « InvestmentFund » n'est pas placé entre crochets, donc MongoDB renvoie tous les documents dans le tableau de produits qui contiennent la valeur spécifiée.

```
db.accounts.find({ products: "InvestmentFund"})
```

## Rechercher un document à l'aide de l'opérateur $elemMatch

Utilisez l' `$elemMatch`opérateur pour rechercher tous les documents qui contiennent le sous-document spécifié. Par exemple :

```
db.sales.find({
  items: {
    $elemMatch: { name: "laptop", price: { $gt: 800 }, quantity: { $gte: 1 } },
  },
})
```

# Recherche de documents à l'aide d'opérateurs logiques

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/S-18abv9IWk"></iframe>

## Recherche de documents à l'aide d'opérateurs logiques

Passez en revue les opérateurs logiques suivants : implicite `$and, $or, and $and.`

## Rechercher un document en utilisant $and implicite

Utilisez implicitement `$and`pour sélectionner des documents correspondant à plusieurs expressions. Par exemple :

```
db.routes.find({ "airline.name": "Southwest Airlines", stops: { $gte: 1 } })
```

## Rechercher un document à l'aide de l'opérateur $or

Utilisez l' `$or`opérateur pour sélectionner les documents qui correspondent à au moins une des expressions incluses. Par exemple :

```
db.routes.find({
  $or: [{ dst_airport: "SEA" }, { src_airport: "SEA" }],
})
```

## Rechercher un document à l'aide de l'opérateur $and

Utilisez l' `$and`opérateur pour utiliser plusieurs expressions $or dans votre requête.

```
db.routes.find({
  $and: [
    { $or: [{ dst_airport: "SEA" }, { src_airport: "SEA" }] },
    { $or: [{ "airline.name": "American Airlines" }, { airplane: 320 }] },
  ]
})
```

# Conclusion

## Opérations CRUD MongoDB : insertion et recherche de documents

Dans cette compétence, vous avez appris à insérer et à rechercher des documents dans une collection MongoDB. Vous avez créé des requêtes en utilisant les opérateurs de comparaison suivants :

$gt (supérieur à)
$lt (inférieur à)
$lte (inférieur ou égal à)
$gte (supérieur ou égal à)

### Vous avez également utilisé les opérateurs logiques suivants :

* et
* $or
  Enfin, vous avez appris comment interroger des éléments dans un tableau et comment utiliser l'opérateur $elemMatch.

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/mGhgB7OBpZM"></iframe>
