# Chapitre : OPERATION CRUD - REMPLACER ET SUPPRIMER DES DOCUMENTS


# Remplacement d'un document dans MongoDB

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/zxf8kR8lfsA"></iframe>

Pour remplacer des documents dans MongoDB, nous utilisons la `replaceOne()`méthode replaceOne() qui prend les paramètres suivants :

* filtre : une requête qui correspond au document à remplacer.
* remplacement : Le nouveau document pour remplacer l'ancien.
* options : un objet qui spécifie les options pour la mise à jour.

Dans la vidéo précédente, nous utilisons le champ **_id** pour filtrer le document. Dans notre document de remplacement, nous fournissons l'intégralité du document qui doit être inséré à sa place. Voici l'exemple de code de la vidéo :

```
db.books.replaceOne(
  {
    _id: ObjectId("6282afeb441a74a98dbbec4e"),
  },
  {
    title: "Data Science Fundamentals for Python and MongoDB",
    isbn: "1484235967",
    publishedDate: new Date("2018-5-10"),
    thumbnailUrl:
      "https://m.media-amazon.com/images/I/71opmUBc2wL._AC_UY218_.jpg",
    authors: ["David Paper"],
    categories: ["Data Science"],
  }
)
```

# Mise à jour des documents MongoDB à l'aide de updateOne()

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/KhC70f8q7BA"></iframe>

La méthode **updateOne(** ) accepte un document de filtre, un document de mise à jour et un objet d'options facultatif. MongoDB fournit des opérateurs et des options de mise à jour pour vous aider à mettre à jour des documents. Dans cette section, nous en aborderons trois :`$set, upsert, and $push.`

## $ensemble

L'opérateur $set remplace la valeur d'un champ par la valeur spécifiée, comme indiqué dans le code suivant :

```
db.podcasts.updateOne(
  {
    _id: ObjectId("5e8f8f8f8f8f8f8f8f8f8f8"),
  },

  {
    $set: {
      subscribers: 98562,
    },
  }
)
```

## insérer

L'option upsert crée un nouveau document si aucun document ne correspond aux critères filtrés. Voici un exemple :

```
db.podcasts.updateOne(
  { title: "The Developer Hub" },
  { $set: { topics: ["databases", "MongoDB"] } },
  { upsert: true }
)
```

## $pousser

L'opérateur $push ajoute une nouvelle valeur au champ du tableau hosts. Voici un exemple :

```
db.podcasts.updateOne(
  { _id: ObjectId("5e8f8f8f8f8f8f8f8f8f8f8") },
  { $push: { hosts: "Nic Raboy" } }
)
```

# Mise à jour des documents MongoDB à l'aide de findAndModify()

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/cWJx5Yxi6RE"></iframe>

La `findAndModify()<span> </span>`méthode est utilisée pour rechercher et remplacer un seul document dans MongoDB. Elle accepte un document de filtre, un document de remplacement et un objet d'options facultatif. Le code suivant montre un exemple :

```
db.podcasts.findAndModify({
  query: { _id: ObjectId("6261a92dfee1ff300dc80bf1") },
  update: { $inc: { subscribers: 1 } },
  new: true,
})
```

# Mise à jour des documents MongoDB à l'aide de updateMany()

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/ilKl_r5Gzp8"></iframe>

Pour mettre à jour plusieurs documents, utilisez la `updateMany()`méthode . Cette méthode accepte un document de filtre, un document de mise à jour et un objet d'options facultatif. Le code suivant montre un exemple :

```
db.books.updateMany(
  { publishedDate: { $lt: new Date("2019-01-01") } },
  { $set: { status: "LEGACY" } }
)
```

# Suppression de documents dans MongoDB

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/NgTRWGQLmiA"></iframe>

Pour supprimer des documents, utilisez les méthodes **deleteOne()** ou **deleteMany()** . Les deux méthodes acceptent un document filtre et un objet options.

## Supprimer un document

Le code suivant montre un exemple de la méthode deleteOne() :

`db.podcasts.deleteOne({ _id: Objectid("6282c9862acb966e76bbf20a") })`

## Supprimer de nombreux documents

Le code suivant montre un exemple de la méthode deleteMany() :

`db.podcasts.deleteMany({category: “crime”})`

# Conclusion

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/ldU1N8Wzo20"></iframe>

## Opérations CRUD MongoDB : remplacer et supprimer des documents

Dans cette compétence, vous avez appris à modifier les résultats de requête avec MongoDB. Plus précisément, vous devez :

* Remplacé un seul document en utilisant db.collection.replaceOne().
* Mise à jour d'une valeur de champ à l'aide de l'opérateur de mise à jour $set dans db.collection.updateOne().
* Ajout d'une valeur à un tableau en utilisant l'opérateur de mise à jour $push dans db.collection.updateOne().
* Ajout d'une nouvelle valeur de champ à un document en utilisant l'option upsert dans db.collection.updateOne().
* J'ai trouvé et modifié un document en utilisant db.collection.findAndModify().
* Mise à jour de plusieurs documents à l'aide de db.collection.updateMany().
* J'ai supprimé un document en utilisant db.collection.deleteOne().
