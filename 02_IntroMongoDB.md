# Chapitre : INTRODUCTION A MONGODB


Dans les compétences suivantes, nous allons apprendre :

* Comment installer MongoDB.
* Comment gérer notre base de données.
* Les meilleures façons de créer, interroger, mettre à jour et supprimer des documents dans MongoDB.

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/xxrY3Breyzo?list=PL-w_yrNy8uTZTI4jXxSqCG_KvtaDphT95"></iframe>

# Définition de MongoDB

**MongoDB est une base de données NoSQL** orientée objet, simple, dynamique et évolutive . Elle est basée sur le modèle de stockage de documents NoSQL où les objets de données sont stockés sous forme de documents séparés et flexibles de **type JSON** . Les objets de données sont stockés dans une collection au lieu de colonnes et de lignes comme dans une base de données relationnelle traditionnelle. Cela signifie que les champs peuvent différer d'un document à l'autre et que la structure des données peut être modifiée au fil du temps.
L'objectif et le but de MongoDB sont d'offrir un magasin de données à hautes performances, à haute disponibilité et à mise à l'échelle horizontale. MongoDB est facile à installer et gratuit à utiliser.
Les versions publiées avant le 16 octobre 2018 sont publiées sous l'AGPL et ses distributions générales prennent en charge Windows, Linux, Mac OS X et Solaris.

![](https://eladnava.com/content/images/2016/07/mongodb-1.jpg)

# Pourquoi utiliser MongoDB est-il mieux que MySQL ? 🤔

Les organisations de toutes tailles choisissent MongoDB car il les aide à créer des applications plus rapidement et à gérer différents types de données. Il les aide également à gérer les applications plus efficacement en fonction de la taille du projet.

Le développement est désormais simplifié avec MongoDB. En effet, les documents MongoDB s'intègrent naturellement aux langages de programmation modernes et orientés objet.

L'utilisation de MongoDB permet de supprimer la couche complexe de mappage objet-relationnel (ORM) qui traduit les objets du code en tables relationnelles. De plus, le modèle de données flexible de MongoDB signifie que votre base de données peut évoluer et répondre aux exigences de l'entreprise.

La structure relationnelle rigide et inflexible de MySQL ajoute des frais aux applications et ralentit les développeurs car ils doivent adapter les objets du code à la structure relationnelle.

# Quelques mots clés avant de commencer

Durant ce cours, nous allons utiliser quelques termes techniques. Il est donc préférable de les définir avant de commencer :
**Schéma :** Un schéma de base de données est la structure squelette qui représente la vue logique de l'ensemble de la base de données. Il définit comment les données sont organisées et comment les relations entre elles sont associées. Il formule toutes les règles qui doivent être appliquées aux données. C'est comme un plan ou une feuille de route qui guide l'utilisateur.
**Document :** le document est l'unité qui est stockée dans la base de données MongoDB. Le document utilise le format de données JSON (JavaScript Object Notation, un format léger et entièrement explorable utilisé pour échanger des données entre différentes applications). Nous pouvons le considérer comme une ligne dans une feuille Excel.
**Collection :** une collection est l'endroit où les documents sont stockés. Nous pouvons le comparer à la feuille Excel qui contient de nombreuses lignes.
![](https://www.w3resource.com/w3r_images/mongodb-document-collection.png)

# Principaux avantages de l'utilisation de MongoDB

**Schema less** − MongoDB is a document database in which one collection holds different documents. The number of fields, content and size of the document can differ from one document to another. Optionally, schema validation can be used to apply data governance controls over each collection.
**Deep query-ability.** MongoDB supports dynamic queries on documents using a document-based query language that is called MongoDB Query Language (MQL). It is nearly as powerful as SQL.
**Higher Availability** − MongoDB automatically replicates your data to additional nodes for high availability and security. In the event of a system failure, the procedure of failover completes automatically - typically in less than 5 seconds.
**Faster Development:** MongoDB’s document data model maps naturally to objects in application code, making it simple for developers to learn and use.
**Scale Infinitely and Cheaply (Ease of scale-out)** − MongoDB includes native support for distributing or sharding a database across any number of commodity machines in a way that is clear to the application.

![](https://learning.naukri.com/articles/wp-content/uploads/sites/11/2017/07/mongoDB.jpg)

# Installation ⚙️

MongoDB is available in two server editions: Community and Enterprise. MongoDB Enterprise provides various features that not available in the MongoDB Community edition, such as In-Memory Storage Engine, Auditing, Kerberos Authentication…

For learning purposes, MongoDB Community edition meets our requirements a lot more than its different counterpart. That's why in this section, we will cover the installation on both Windows and Linux (Ubuntu) operating systems. If you have a different OS, you can refer to the [official documentation](https://docs.mongodb.com/manual/installation/) where you can find tutorials for all supported distributions.

To install MongoDB on windows OS, you only have to visit the website and follow the instructions.

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/zVBUE4gWD3o"></iframe>

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/k0Co2NSqnbI"></iframe>
