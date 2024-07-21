Insertion de documents dans une collection MongoDB

Examinez le code suivant, qui montre comment inserer un seul document et plusieurs documents dans une collection MongoDB

- Inserer un seul document 
        La methode insertOne() permet d'inserer un document dans une collection. Entre les parenthèses de insertOne(),
        incluez un objet qui contient des données du document.

        db.grades.insertOne(
            {
                student_id:63245,
                products:[
                    {
                        type:"exam",
                        score:90,
                    },
                    {
                        type:"homework",
                        score:90,
                    },
                    {
                        type:"quiz",
                        score:75,
                    },
                    {
                        type:"homework",
                        score:88,
                    },
                ],
                class_id: 550,
        })

- Inserer plusieurs documents
        La methode insertMany() permet d'inserer plusieurs documents à la fois. Dans la insertMany()
        incluez les documents dans un tableau. Chaque document doit être séparé par une virgule.

        bd.grades.insertMany([
            {
                student_id: 546789,
                products: [
                    {
                        type:"quiz",
                        score:50,
                    },
                    {
                        type:"homework",
                        score:70,
                    },
                    {
                        type:"quiz",
                        score:66,
                    },
                    {
                        type:"exam",
                        score:70,
                    },
                ],
                class_id:551
            },
            {
                student_id: 777777,
                products: [
                    {
                        type:"exam",
                        score:83,
                    },
                    {
                        type:"quiz",
                        score:59,
                    },
                    {
                        type:"quiz",
                        score:72,
                    },
                    {
                        type:"quiz",
                        score:67,
                    },
                ],
                class_id: 550,
            },
            {
                student_id: 223344,
                products: [
                    {
                        type:"exam",
                        score:45,
                    },
                    {
                        type:"homework",
                        score:39,
                    },
                    {
                        type:"quiz",
                        score:40,
                    },
                    {
                        type:"homework",
                        score:88,
                    },
                ],
                class_id: 551,
            }
        ])        


- Recherche des documents dans une collection MongoDB 
    * Trouver un document avec égalité
      Lorsque l'égalité avec un champ _id est donnée, la commande find() 
      renvoie le document spécifié qui correspond à _id. 
        
        Exemple : db.zips.find({_id: ObjectId("5c8eccc1caa187d17ca6ed16")})

    * Rechercher un document à l'aide de l'operateur $in 
      Utiliser l'opérateur $in pour selectionner les documents dans lesquels la valeur d'un champ 
      est égale à n'importe quelle valeur du tableau spécifié.

        Exemple : db.zips.find({ city: { $in: ["PHOENIX", "CHICAGO"]}})  

    * Recherche de documents à l'aide d'opérateurs de comparaison
      Passez en revue les opérateurs de comparaison suivants : $gt, $lt, $lte,et $gte. 

      - $gt
        Utilisez l'opérateur $gt pour faire correspondre les documents avec un 
        champ supérieur à la valeur donnée. 
        Par exemple : db.sales.find({ "items.price": { $gt: 50}})     

      - $lt
        Utilisez l'opérateur $lt pour faire correspondre les documents avec un 
        champ inférieur à la valeur donnée. 
        Par exemple : db.sales.find({ "items.price": { $lt: 50}})

      - $lte
        Utilisez l'opérateur $lte pour faire correspondre les documents avec un 
        champ inférieur ou égal à la valeur donnée. 
        Par exemple : db.sales.find({ "customer.age": { $lte: 65}}) 

      - $gte
        Utilisez l'opérateur $gte pour faire correspondre les documents avec un 
        champ supérieur ou égal à la valeur donnée. 
        Par exemple : db.sales.find({ "customer.age": { $gte: 65}})            

- Rechercher des documents avec un tableau contenant une valeur spécifiée
        Dans l'exemple suivant, « InvestmentFund » n'est pas placé entre crochets, donc MongoDB renvoie tous les documents dans le tableau de produits qui contiennent la valeur spécifiée.
        Exemple : db.accounts.find({ products: "InvestmentFund"})

    * Rechercher un document à l'aide de l'opérateur $elemMatch Utilisez l' $elemMatchopérateur pour rechercher tous les documents qui contiennent le sous-document spécifié. Par exemple :
    db.sales.find({
        items: {
            $elemMatch: { name: "laptop", price: { $gt: 800 }, quantity: { $gte: 1 } },
        },
    }) 

    Recherche de documents à l'aide d'opérateurs logiques
    Passez en revue les opérateurs logiques suivants : implicite$and, $or, and $and.
    
    Rechercher un document en utilisant $and implicite
    Utilisez implicitement $andpour sélectionner des documents correspondant à plusieurs expressions. 
    Par exemple : 
        db.routes.find({ "airline.name": "Southwest Airlines",stops: { $gte: 1 } })

    Rechercher un document à l'aide de l'opérateur $or
    Utilisez l' $oropérateur pour sélectionner les documents qui correspondent à au moins une des expressions incluses. 
    Par exemple :
        db.routes.find({
            $or: [{ dst_airport: "SEA" }, { src_airport: "SEA" }],
            })

    Rechercher un document à l'aide de l'opérateur $and
    Utilisez l' $andopérateur pour utiliser plusieurs expressions $or dans votre requête.
        db.routes.find({
            $and: [
                { $or: [{ dst_airport: "SEA" }, { src_airport: "SEA" }] },
                { $or: [{ "airline.name": "American Airlines" }, { airplane: 320 }] },
            ]
        })       