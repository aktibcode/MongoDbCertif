1-  Utilisation de la recherche basée sur la pertinence et des index de recherche

        https://youtu.be/5T6zMZeeqew


2-  Créer un index de recherche avec mappage dynamique

        https://youtu.be/tDWKcAzPeZk


3-  Créer un index de recherche avec mappage de champs statiques

        https://youtu.be/E8yWDhObfwU


4-  Utilisation de $search et des opérateurs composés

        https://youtu.be/SpGEbQZcRfE

    L'opérateur composé dans l'étape d'agrégation $search nous permet de donner du poids 
    à différents champs et également de filtrer nos résultats sans avoir à créer d'étapes 
    d'agrégation supplémentaires. Les quatre options de l'opérateur composé sont 
    « must », « mustNot », « should » et « filter ».

    « must » exclura les enregistrements qui ne répondent pas aux critères. « mustNot »
     exclura les résultats qui répondent aux critères. « should » vous permettra de donner 
     du poids aux résultats qui répondent aux critères afin qu'ils apparaissent en premier.
      « filter » supprimera les résultats qui ne répondent pas aux critères.
      
        $search {
        "compound": {
            "must": [{
                "text": {
                    "query": "field",
                    "path": "habitat"
                }
            }],
            "should": [{
                "range": {
                    "gte": 45,
                    "path": "wingspan_cm",
                    "score": {"constant": {"value": 5}}
                }
            }]
            }
        }

5-  Regroupement des résultats de recherche à l'aide de facettes

    https://youtu.be/3Ss8aJWyoxs

    *   $searchMeta et facette

    $searchMeta est une étape d'agrégation pour Atlas Search où les métadonnées 
    liées à la recherche sont affichées. Cela signifie que si nos résultats de recherche 
    sont divisés en compartiments, à l'aide de la facette, nous pouvons le voir 
    dans l'étape $searchMeta, car ces compartiments contiennent des informations sur 
    la façon dont les résultats de recherche sont formatés.

        $searchMeta: {
            "facet": {
                "operator": {
                    "text": {
                    "query": ["Northern Cardinal"],
                    "path": "common_name"
                    }
                },
                "facets": {
                    "sightingWeekFacet": {
                        "type": "date",
                        "path": "sighting",
                        "boundaries": [ISODate("2022-01-01"), 
                            ISODate("2022-01-08"),
                            ISODate("2022-01-15"),
                            ISODate("2022-01-22")],
                        "default" : "other"
                    }
                }
            }
        }

        « facet » est un opérateur dans $searchMeta. « operator » fait référence à l'opérateur 
        de recherche - la requête elle-même. L'opérateur « facettes » est l'endroit 
        où nous plaçons la définition des buckets pour les facettes.

Conclusion

Recherche Atlas MongoDB

    Félicitations pour votre découverte d'Atlas Search, un outil incroyablement puissant 
    pour ajouter des fonctionnalités de recherche à vos applications. Dans cette compétence, 
    nous avons abordé les bases d'Atlas Search, notamment les suivantes :

    *   Qu'est-ce qu'un index de recherche.

    Comment utiliser un index de recherche mappé dynamiquement pour trouver des résultats à 
    partir de n'importe quel champ de vos données.

    *   Comment utiliser un index de recherche mappé statiquement pour trouver des résultats à 
    partir des parties les plus pertinentes de vos données.

    *   Comment utiliser le pipeline d'agrégation pour terminer une opération $search.

    *   Comment utiliser un opérateur composé pour effectuer une recherche basée sur plusieurs opérateurs.

    *   Comment utiliser un opérateur composé pour donner plus de poids à certains champs et 
    donner à l'utilisateur des résultats plus pertinents.

    *   Comment utiliser $searchMeta et $facet pour catégoriser les résultats de 
    recherche afin d'aider les utilisateurs de votre application à trouver plus rapidement ce dont ils ont besoin

        https://youtu.be/3lCPqx7KzJ0


