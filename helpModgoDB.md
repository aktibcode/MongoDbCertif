Classe de base de données :

    -   getMongo ---------------    Renvoie la connexion actuelle à la base de données

    -   getName  ---------------    Renvoie le nom de la base de données
    
    -   getCollectionNames --------------- Renvoie un tableau contenant les noms de 
                                           toutes les collections de la base de données actuelle.

    -   getCollectionInfos --------------- Renvoie un tableau de documents avec des informations sur 
                                           la collection, c'est-à-dire le nom et les options de 
                                           la - collection, pour la base de données actuelle.

    -   runCommand -------------    Exécute une commande arbitraire sur la base de données.

    -   adminCommand -----------    Exécute une commande arbitraire sur la base de données admin.

    -   global -----------------    Exécute un pipeline d'administration/diagnostic spécifié 
                                    qui ne nécessite pas de collection sous-jacente.

    -   getSiblingDB Renvoie une autre base de données sans modifier la variable db dans l'environnement shell.
    
    -   getCollection Renvoie une collection ou un objet de vue dont la fonctionnalité est équivalente 
                      à l'utilisation de db.<collectionName>.

    -   dropDatabase Supprime la base de données actuelle, en supprimant les fichiers de données associés.

    -   createUser Crée un nouvel utilisateur pour la base de données sur laquelle la méthode est exécutée. 
    
    -   db.createUser() renvoie une erreur d'utilisateur en double si l'utilisateur existe déjà dans la base de données.
    
    -   updateUser Met à jour le profil des utilisateurs sur la base de données sur laquelle vous exécutez la méthode. 
                    Une mise à jour d'un champ remplace complètement les valeurs des champs précédents.
                    Cela inclut les mises à jour du tableau des rôles des utilisateurs.

    -   changeUserPassword Met à jour le mot de passe d'un utilisateur. Exécutez la méthode dans la 
                    base de données où l'utilisateur est défini, c'est-à-dire la base de données 
                    dans laquelle vous avez créé l'utilisateur.

    -   logout Termine la session d'authentification en cours. Cette fonction 
                    n'a aucun effet si la session en cours n'est pas authentifiée.

    -   dropUser Supprime l'utilisateur de la base de données actuelle.

    -   dropAllUsers Supprime tous les utilisateurs de la base de données actuelle.

    -   auth Permet à un utilisateur de s'authentifier auprès de la base de données depuis le shell.

    -   grantRolesToUser Accorde des rôles supplémentaires à un utilisateur.

    -   revokeRolesFromUser Supprime un ou plusieurs rôles d'un utilisateur sur la base de données actuelle.

    -   getUser Renvoie les informations utilisateur pour un utilisateur spécifié. 
                    Exécutez cette méthode sur la base de données des utilisateurs. 
                    L'utilisateur doit exister sur la base de données sur laquelle la méthode s'exécute.

    -   getUsers Renvoie des informations sur tous les utilisateurs de la base de données.

    -   createCollection Créer une nouvelle collection

    -   createEncryptedCollection Crée une nouvelle collection avec une liste de champs chiffrés, 
                    chacun avec des clés de chiffrement de données (DEK) uniques et créées automatiquement. 
                    Il s'agit d'une fonction utilitaire qui utilise en interne ClientEnryption.createEncryptedCollection.

    -   createView Créer une nouvelle vue

    -   createRole Crée un nouveau rôle.

    -   updateRole Met à jour le profil des rôles sur la base de données 
                    sur laquelle vous exécutez la méthode. Une mise à jour d'un champ remplace 
                    complètement les valeurs des champs précédents.

    -   dropRole Supprime le rôle de la base de données actuelle.

    -   dropAllRoles Supprime tous les rôles de la base de données actuelle.

    -   grantRolesToRole Accorde des rôles supplémentaires à un rôle.

    -   revokeRolesFromRole Supprime un ou plusieurs rôles d'un rôle sur la base de données actuelle.

    -   grantPrivilegesToRole Accorde des privilèges supplémentaires à un rôle.

    -   revokePrivilegesFromRole Supprime un ou plusieurs privilèges d'un rôle sur la base de données actuelle.

    -   getRole Renvoie les informations sur le rôle pour un rôle spécifié. 
                Exécutez cette méthode sur la base de données des rôles. 
                Le rôle doit exister sur la base de données sur laquelle la méthode s'exécute.

    -   getRoles Renvoie des informations sur tous les rôles de la base de données.

    -   currentOp Exécute une agrégation à l'aide de l'opérateur $currentOp. 
                Renvoie un document contenant des informations sur les opérations en cours pour 
                l'instance de base de données. Pour plus d’informations, consultez $currentOp.

    -   killOp Appelle la commande killOp. Termine une opération comme spécifié par l'ID d'opération. 
                Pour rechercher les opérations et leurs identifiants correspondants, 
                consultez $currentOp ou db.currentOp().
    
    -   shutdownServer Appelle la commande shutdown. Arrête le processus mongod ou mongos 
                actuel de manière propre et sûre. Vous devez exécuter l'opération db.shutdownServer() 
                sur la base de données admin.
  