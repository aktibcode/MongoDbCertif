A- Index MongoDB
    (Cours intéressant)
    https://youtu.be/hL-UCOxfCq8
    https://rtavenar.github.io/mongo_book/content/00_intro.html

B- Création d'un index à Champ unique
    https://youtu.be/qFN6qOuFUEI

    Consultez le code ci-dessous, qui montre comment créer un index de champ unique dans une collection.

C- Créer un index à champ unique
        Permet createIndex()de créer un nouvel index dans une collection. Entre les parenthèses de createIndex(), incluez un objet contenant le champ et l'ordre de tri.

            db.customers.createIndex({
            birthdate: 1
            })
D- Créer un index unique à champ unique
        Ajoutez {unique:true}un second paramètre facultatif dans createIndex() pour forcer l'unicité des valeurs des champs d'index. Une fois l'index unique créé, toutes les insertions ou mises à jour incluant des valeurs dupliquées dans la collection pour le ou les champs d'index échoueront.

        db.customers.createIndex({
            email: 1
        },
        {
            unique:true
        })
    MongoDB crée l'index unique uniquement s'il n'y a pas de duplication dans les valeurs de champ pour le/les champ(s) d'index.

E- Afficher les index utilisés dans une collection
        Permet getIndexes() de voir tous les index créés dans une collection.

        db.customers.getIndexes()
    
    *  Vérifier si un index est utilisé dans une requête
        Utiliser explain()dans une collection lors de l'exécution d'une requête pour voir le plan d'exécution. 
        Ce plan fournit les détails des étapes d'exécution (IXSCAN, COLLSCAN, FETCH, SORT, etc.).

        - L' étape IXSCAN indique que la requête utilise un index et quel index est sélectionné.
        - L' étape COLLSCAN indique qu'une analyse de collection est effectuée, sans utiliser d'index.
        - L' étape FETCH indique que les documents sont en cours de lecture à partir de la collection.
        - L' étape SORT indique que les documents sont triés en mémoire.

        db.customers.explain().find({
            birthdate: {
                $gt:ISODate("1995-08-01")
            }
        })
        db.customers.explain().find({
            birthdate: {
                $gt:ISODate("1995-08-01")
            }
        }).sort({
            email:1
        })


F- Comprendre les index multi-clés

        https://youtu.be/Civ908Eav_A
    Consultez le code ci-dessous, qui montre comment fonctionnent les index multiclés. Si un champ unique ou un index composé inclut un champ de tableau, l'index est alors un index multiclé.

    *   Créer un index multi-clés à champ unique
            Permet createIndex()de créer un nouvel index dans une collection. 
            Inclure un objet comme paramètre contenant le champ de tableau et l'ordre de tri. 
            Dans cet exemple, les comptes sont un champ de tableau.

            db.customers.createIndex({
                accounts: 1
            })

    *   Afficher les index utilisés dans une collection
            Utilisez getIndexes() pour voir tous les index créés dans une collection.

            db.customers.getIndexes()      

    *   Vérifier si un index est utilisé dans une requête
            Utilisez la fonction describe() dans une collection lors de l'exécution d'une requête pour voir le plan d'exécution. 
            Ce plan fournit les détails des étapes d'exécution (IXSCAN, COLLSCAN, FETCH, SORT, etc.).

            -   L' étape IXSCAN indique que la requête utilise un index et quel index est sélectionné.
            -   L' étape COLLSCAN indique qu'une analyse de collection est effectuée, sans utiliser d'index.
            -   L' étape FETCH indique que les documents sont en cours de lecture à partir de la collection.
            -   L' étape SORT indique que les documents sont triés en mémoire. 
        
            db.customers.explain().find({
                accounts: 627788
            })     

G-  Travailler avec des index composés

            https://youtu.be/rxPjWIeuzLs

       Consultez le code ci-dessous, qui montre comment créer un index composé dans une collection.
    
H-  Créer un index composé

    Permet createIndex()de créer un nouvel index dans une collection. Entre les parenthèses de createIndex(), 
    incluez un objet contenant deux champs ou plus et leur ordre de tri.

        db.customers.createIndex({
            active:1, 
            birthdate:-1,
            name:1
        }) 

I-  Ordre des champs dans un index composé

    L'ordre des champs est important lors de la création de l'index et de l'ordre de tri. Il est recommandé de répertorier les champs dans l'ordre suivant : Égalité, Tri et Plage.

    -   Égalité : champ(s) qui correspondent à une seule valeur de champ dans une requête
    -   Trier : champ(s) qui ordonnent les résultats dans une requête
    -   Plage : champ(s) que la requête filtre dans une plage de valeurs valides
    La requête suivante inclut une correspondance d'égalité sur le champ actif, un tri sur l'anniversaire (décroissant) et le nom (croissant), ainsi qu'une requête de plage sur l'anniversaire également.

        db.customers.find({
            birthdate: {
                $gte:ISODate("1977-01-01")
            },
            active:true
            }).sort({
                birthdate:-1, 
                name:1
        })   

            Voici un exemple d’index efficace pour cette requête :

                db.customers.createIndex({
                    active:1, 
                    birthdate:-1,
                    name:1
                })
                Afficher les index utilisés dans une collection
                Utilisez cette option getIndexes()pour voir tous les index créés dans une collection.

                db.customers.getIndexes()       

J-  Vérifier si un index est utilisé dans une requête

    Utilisez la fonction describe() dans une collection lors de l'exécution d'une requête pour voir le plan d'exécution. Ce plan fournit les détails des étapes d'exécution (IXSCAN, COLLSCAN, FETCH, SORT, etc.). En voici quelques exemples :

    -   L' étape IXSCAN indique que la requête utilise un index et quel index est sélectionné.
    -   L' étape COLLSCAN indique qu'une analyse de collection est effectuée, sans utiliser d'index.
    -   L' étape FETCH indique que les documents sont en cours de lecture à partir de la collection.
    -   L' étape SORT indique que les documents sont triés en mémoire. 

        db.customers.explain().find({
            birthdate: {
                $gte:ISODate("1977-01-01")
            },
            active:true
        }).sort({
            birthdate:-1,
            name:1
        })

K-  Couvrir une requête par l'index

    Un index couvre une requête lorsque MongoDB n'a pas besoin de récupérer les données de la mémoire puisque toutes les données requises sont déjà renvoyées par l'index.

    Dans la plupart des cas, nous pouvons utiliser des projections pour renvoyer uniquement les champs requis et couvrir la requête. Assurez-vous que les champs de la projection se trouvent dans l'index.

    En ajoutant la projection {name:1,birthdate:1,_id:0} dans la requête précédente, nous pouvons limiter les champs renvoyés au nom et à la date de naissance uniquement. Ces champs font partie de l'index et lorsque nous exécutons la commande explanation(), le plan d'exécution ne montre que deux étapes :

    -   IXSCAN - Analyse d'index à l'aide de l'index composé
    -   PROJECTION_COVERED - Toutes les informations nécessaires sont renvoyées par l'index, pas besoin de les récupérer en mémoire

        db.customers.explain().find(
            {
            birthdate: {
                $gte:ISODate("1977-01-01")
            },
                active:true
            },
            {
                name:1,
                birthdate:1, 
                _id:0
        }).sort(
            {
                birthdate:-1,
                name:1
            }
        )

L-  Suppression d'un index

    https://youtu.be/bu_CXvigOHg

    Consultez le code ci-dessous, qui montre comment supprimer des index dans une collection.

M-  Afficher les index utilisés dans une collection

    Utilisez getIndexes() pour voir tous les index créés dans une collection. Il existe toujours un index par défaut dans chaque collection sur le champ _id. Cet index est utilisé par MongoDB en interne et ne peut pas être supprimé.

        db.customers.getIndexes()

N-  Supprimer un index

    Permet dropIndex()de supprimer un index existant d'une collection. Dans les parenthèses de dropIndex(), incluez un objet représentant la clé d'index ou indiquez le nom de l'index sous forme de chaîne. 

O-  Supprimer l'index par nom :
        
        db.customers.dropIndex(
            'active_1_birthdate_-1_name_1'
        )

P-  Supprimer l'index par clé :

        db.customers.dropIndex({
            active:1,
            birthdate:-1, 
            name:1
        })

Q-  Supprimer les index

    Utilisez dropIndexes() pour supprimer tous les index d'une collection, à l'exception de l'index par défaut sur _id.

        db.customers.dropIndexes()

    La commande dropIndexes() peut également accepter un tableau de noms d'index comme paramètre pour supprimer une liste spécifique d'index.

        db.collection.dropIndexes([
            'index1name', 'index2name', 'index3name'
        ])

Conclusion
    Index MongoDB
        Dans cette compétence, nous avons appris ce que sont les index et comment ils améliorent les performances. Nous avons examiné et créé différents index :

        Champ unique (un champ)
        Composé (2 à 32 champs)
    Nous avons travaillé avec des propriétés d’index telles que unique et avons compris que les index multiclés sont des index qui incluent un champ de tableau.
    
    Nous avons utilisé les commandes suivantes dans la collection pour créer ou supprimer des index :

        -   créerIndex()
        -   dropIndex()
    Enfin, nous avons appris comment afficher les index utilisés dans une collection avec la commande getIndexes() et comment vérifier si l'index est utilisé dans une requête en exécutant la commande explicit().

    https://youtu.be/Nd4t_dCti4g

