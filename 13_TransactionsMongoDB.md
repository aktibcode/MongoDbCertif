1-  Introduction aux transactions ACID

        https://youtu.be/NPXp1VLMt8k


2-  Transactions ACID dans MongoDB

        https://youtu.be/KtqxuQ0Y0fE


3- Utilisation des transactions dans MongoDB

        https://youtu.be/k9KTHQlrqx8


4- Transactions multi-documents

    Les transactions ACID dans MongoDB sont généralement utilisées uniquement par 
    les applications où des valeurs sont échangées entre différentes parties, 
    telles que les applications bancaires ou commerciales. Si vous vous trouvez 
    dans un scénario où une transaction multi-document est requise, il est très probable 
    que vous effectuiez une transaction avec l'un des pilotes de MongoDB. Pour l'instant, 
    concentrons-nous sur la réalisation et l'annulation de transactions multi-documents 
    dans le shell pour nous familiariser avec les étapes.

    -   Utilisation d'une transaction : code vidéo

        Voici un récapitulatif du code utilisé pour effectuer une transaction multi-documents :

            const session = db.getMongo().startSession()

            session.startTransaction()

            const account = session.getDatabase('< add database name here>')
                                   .getCollection('<add collection name here>')

            //Add database operations like .updateOne() here

            session.commitTransaction()

5-  Annuler une transaction

    Si vous vous trouvez dans une situation qui nécessite d'annuler des opérations de base de données 
    avant la fin d'une transaction, vous pouvez interrompre la transaction. Cela ramènera la base de 
    données à son état d'origine, avant le lancement de la transaction.

    -   Annuler une transaction : code vidéo

        Here is a recap of the code that's used to cancel a transaction before it completes:

        const session = db.getMongo().startSession()

        session.startTransaction()

        const account = session.getDatabase('< add database name here>').getCollection('<add collection name here>')

        //Add database operations like .updateOne() here

        session.abortTransaction()


Conclusion

        https://youtu.be/4bI-j4zouaM

Transactions MongoDB

    Dans cette compétence, vous avez appris que les transactions ACID garantissent que les opérations
    de base de données, telles que le transfert de fonds d'un compte à un autre, se produisent ensemble ou pas du tout. 
    Vous avez également exploré le fonctionnement des transactions ACID avec le modèle de document dans MongoDB. 
    Enfin, vous avez appris à créer et à utiliser des transactions multi-documents à l'aide des commandes startTransaction() 
    et commitTransaction(), et à annuler des transactions multi-documents à l'aide de la commande abortTransaction().
