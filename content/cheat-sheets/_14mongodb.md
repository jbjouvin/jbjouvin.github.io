+++ 
date = "1979-01-01"
title = "mongodb"
description = "mongodb"
+++


<h2 id=MongoDB>MongoDB
<img src="https://pbs.twimg.com/profile_images/750403034178478081/EPrK3ci2.jpg" height="100" width="100" align="right">
</h2>

```mongodb
MongoDB
```

#### Commandes essentiels

[https://buzut.fr/commandes-de-base-de-mongodb/](https://buzut.fr/commandes-de-base-de-mongodb/)

##### 1 - Importez le jeu de données tour-pedia.json dans une base de données “tourPedia” avec une collection “paris” ;
```
mongoimport --db tourPedia --collection paris --file /tmp/tourPedia_paris.json
```
##### 2 - Filtrez les lieux par type “accommodation” et service “blanchisserie” ;

```
db.getCollection('paris').find({"category":"accommodation", "services":"blanchisserie"});
```
##### 3 - Projetez les adresses des lieux de type "accommodation" ;

```
db.getCollection('paris').find({"category":"accommodation"},{"location.address": 1, "_id":0});
```
##### 4 - Filtrez les listes de commentaires (reviews) des lieux, pour lesquelles au moins un commentaire (reviews) est écrit en anglais (en) et a une note (rating) supérieure à 3 (attention, LE commentaire en anglais doit avoir un rang de 3 ou plus) ;

```
db.paris.find({"reviews": {
                           $elemMatch: {
                              "language":"en",
                               "rating":{$gt:3}
                               } 
                           } 
               }, {"reviews": 1});
```
##### 5 - Groupez les lieux par catégorie et comptez les ;
```
varGroup = { $group : {"_id" : "$category", "somme":{$sum:1}}};
db.paris.aggregate( [ varGroup ]);
```
##### 6 - Créez un pipeline d’agrégation pour les lieux de catégorie "accommodation", et donnez le nombre de lieux par valeur de "services".

```
varMatch = {$match: {"category":"accommodation"}};
varServiceUnwind = {$unwind : "$services"};
varGroup2 = { $group : {"_id" : "$services", "nbre_lieux" : {$sum : 1} } };
varSort = { $sort : { "nbre_lieux" : -1 } };
db.paris.aggregate( [ varServiceUnwind, varMatch, varGroup2, varSort ] );
```

