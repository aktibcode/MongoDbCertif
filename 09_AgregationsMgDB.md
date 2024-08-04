# Chapitre : AGREGATIONS MONGODB


# Introduction à l'agrégation MongoDB

## Définitions

* **Agrégation** : Collecte et synthèse des données
* **Étape :** l'une des méthodes intégrées qui peuvent être appliquées aux données, mais qui ne les modifie pas de manière permanente
* **Pipeline d'agrégation :** une série d'étapes réalisées sur les données afin

## Structure d'un pipeline d'agrégation

```
db.collection.aggregate([
    {
        $stage1: {
            { expression1 },
            { expression2 }...
        },
        $stage2: {
            { expression1 }...
        }
    }
])
```

# Utilisation des étapes $match et $group dans un pipeline d'agrégation MongoDB

Consultez les sections suivantes, qui présentent le code des étapes d’agrégation `$match`et de `$group`.

### $correspond

L'étape $match filtre les documents qui correspondent aux conditions spécifiées. Voici le code de $match :

```
{
  $match: {
     "field_name": "value"
  }
}
```

### $groupe

L'étape $group regroupe les documents par une clé de groupe.

```
{
  $group:
    {
      _id: <expression>, // Group key
      <field>: { <accumulator> : <expression> }
    }
 }
```

### $match et $group dans un pipeline d'agrégation

Le pipeline d'agrégation suivant recherche les documents avec un champ nommé « état » qui correspond à une valeur « CA », puis regroupe ces documents par la clé de groupe « $city » et affiche le nombre total de codes postaux dans l'État de Californie.

```
db.zips.aggregate([
{   
   $match: { 
      state: "CA"
    }
},
{
   $group: {
      _id: "$city",
      totalZips: { $count : { } }
   }
}
])
```

# Utilisation des étapes $sort et $limit dans un pipeline d'agrégation MongoDB

Consultez les sections suivantes, qui montrent le code des étapes d’agrégation $sort et $limit.

### $trier

L'étape $sort trie tous les documents d'entrée et les renvoie au pipeline dans l'ordre trié. Nous utilisons 1 pour représenter l'ordre croissant et -1 pour représenter l'ordre décroissant.

```
{
    $sort: {
        "field_name": 1
    }
}
```

### $limit

L'étape $limit renvoie uniquement un nombre spécifié d'enregistrements.

```
{
  $limit: 5
}
```

$sort et $limit dans un pipeline d'agrégation
Le pipeline d'agrégation suivant trie les documents par ordre décroissant, de sorte que les documents avec la plus grande valeur pop apparaissent en premier, et limite la sortie aux cinq premiers documents uniquement après le tri.

```
db.zips.aggregate([
{
  $sort: {
    pop: -1
  }
},
{
  $limit:  5
}
])
```

# Utilisation des étapes $project, $count et $set dans un pipeline d'agrégation MongoDB

Consultez les sections suivantes, qui présentent le code des étapes d’agrégation $project, $set et $count.

### $projet

L'étape $project spécifie les champs des documents de sortie. 1 signifie que le champ doit être inclus et 0 signifie que le champ doit être supprimé. Une nouvelle valeur peut également être attribuée au champ.

```
{
    $project: {
        state:1, 
        zip:1,
        population:"$pop",
        _id:0
    }
}
```

### $ensemble

L'étape $set crée de nouveaux champs ou modifie la valeur des champs existants, puis génère les documents avec les nouveaux champs.

```
{
    $set: {
        place: {
            $concat:["$city",",","$state"]
        },
        pop:10000
     }
  }
```

### $compter

L'étape $count crée un nouveau document, avec le nombre de documents à cette étape dans le pipeline d'agrégation attribué au nom de champ spécifié.

```
{
  $count: "total_zips"
}
```

# Utilisation de l'étape $out dans un pipeline d'agrégation MongoDB

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/9LTdTxAH69Q"></iframe>
