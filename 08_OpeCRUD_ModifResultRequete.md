# Chapitre : MODIFICATION DES RESULTATS DE REQUETE


# Tri et limitation des résultats de requête dans MongoDB

Consultez le code suivant, qui montre comment trier et limiter les résultats de la requête.

## Tri des résultats

Utilisez **cursor.sort()** pour renvoyer les résultats de la requête dans un ordre spécifié. Dans les parenthèses de sort(), incluez un objet qui spécifie le ou les champs à trier et l'ordre du tri. Utilisez 1 pour l'ordre croissant et -1 pour l'ordre décroissant.

Syntaxe:

`db.collection.find(<query>).sort(<sort>)`

Exemple:

```
// Return data on all music companies, sorted alphabetically from A to Z.
db.companies.find({ category_code: "music" }).sort({ name: 1 });
```

Pour garantir que les documents sont renvoyés dans un ordre cohérent, incluez un champ contenant des valeurs uniques dans le tri. Un moyen simple de procéder consiste à inclure le champ **_id** dans le tri. Voici un exemple :

```
// Return data on all music companies, sorted alphabetically from A to Z. Ensure consistent sort order
db.companies.find({ category_code: "music" }).sort({ name: 1, _id: 1 });
```

Limitation des résultats
Permet `cursor.limit()`de spécifier le nombre maximal de documents que le curseur peut renvoyer. Entre les parenthèses de limit(), spécifiez le nombre maximal de documents à renvoyer.

**Syntaxe:**

`db.companies.find(<query>).limit(<number>)`

**Exemple:**

```
// Return the three music companies with the highest number of employees. Ensure consistent sort order.
db.companies
  .find({ category_code: "music" })
  .sort({ number_of_employees: -1, _id: 1 })
  .limit(3);
```

# Renvoyer des données spécifiques à partir d'une requête dans MongoDB

Examinez le code suivant, qui montre comment renvoyer les champs sélectionnés à partir d’une requête.

## Ajouter un document de projection

Pour spécifier les champs à inclure ou à exclure dans l'ensemble de résultats, ajoutez un document de projection comme deuxième paramètre dans l'appel à `db.collection.find()`.

Syntaxe:

`db.collection.find( <query>, <projection> )`
Inclure un champ
Pour inclure un champ, définissez sa valeur sur 1 dans le document de projection.

Syntaxe:

`db.collection.find( <query>, { <field> : 1 })`

Exemple:

```
// Return all restaurant inspections - business name, result, and _id fields only
db.inspections.find(
  { sector: "Restaurant - 818" },
  { business_name: 1, result: 1 }
)
```

Exclure un champ
Pour exclure un champ, définissez sa valeur sur 0 dans le document de projection.

Syntaxe:

`db.collection.find(query, { <field> : 0, <field>: 0 })`
Exemple:

```
// Return all inspections with result of "Pass" or "Warning" - exclude date and zip code
db.inspections.find(
  { result: { $in: ["Pass", "Warning"] } },
  { date: 0, "address.zip": 0 }
)
```

Bien que le champ _id soit inclus par défaut, il peut être supprimé en définissant sa valeur sur 0 dans n'importe quelle projection.

```
// Return all restaurant inspections - business name and result fields only
db.inspections.find(
  { sector: "Restaurant - 818" },
  { business_name: 1, result: 1, _id: 0 }
)
```

# Comptage des documents dans une collection MongoDB

Examinez le code suivant, qui montre comment compter le nombre de documents correspondant à une requête.

## Compter les documents

Utilisé `db.collection.countDocuments()`pour compter le nombre de documents correspondant à une requête. countDocuments() prend deux paramètres : un document de requête et un document d'options.

Syntaxe:

`db.collection.countDocuments( <query>, <options> )`
La requête sélectionne les documents à compter.

Exemples:

```
// Count number of docs in trip collection
db.trips.countDocuments({})
// Count number of trips over 120 minutes by subscribers
db.trips.countDocuments({ tripduration: { $gt: 120 }, usertype: "Subscriber" })
```

# Opérations CRUD MongoDB : modification des résultats de requête

Dans cette compétence, vous avez appris à modifier les résultats de requête avec MongoDB. Plus précisément, vous avez appris à :

* Renvoie les résultats de la requête dans un ordre spécifié en utilisant cursor.sort().
* Limité le nombre de résultats renvoyés en utilisant cursor.limit().
* Champs spécifiés à renvoyer en ajoutant un paramètre de document de projection dans les appels à db.collection.find().
* Comptez le nombre de documents correspondant à une requête en utilisant db.collection.countDocuments().
