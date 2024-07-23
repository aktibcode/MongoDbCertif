OPERATIONS CRUD MongoDB : remplacer et supprimer des documents 

- Remplacement d'un document dans MongoDB.

    Pour remplacer des documents dans MongoDB, nous utilisons la methode replaceOne() qui prend les paramètres suivants :
        * filtre : une requête qui correspond au document à remplacer.
        * remplacement : Le nouveau document pour remplacer l'ancien.
        * options : un objet qui spécifie les options pour la mise à jour.
    Exemple :
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

- Mise à jour des documents MongoDB à l'aide de updateOne()