# projet-python-2A

Ce dépôt est le résultat du travail de Camille Frouard, Caroline Lebrun et Isaure Pillet pour leur projet de deuxième année de l'Ensae (novembre 2024 - janvier 2025).


# Table des matières
1. [Intérêt du sujet](#interet)
2. [Objectifs](#objectifs)
3. [Sources des données](#sources)
4. [Présentation du dépôt](#pres)
5. [Licence](#licence)



## 1. Intérêt du sujet <a name="interet">
Depuis le 25 novembre 2024, un dispositif d'encadrement des loyers est entré en vigueur dans 24 communes du Pays Basque. Face à une hausse du prix d'achat au m² de 35% entre 2019 et 2023, cette mesure valable pour une durée de deux ans a pour objectif de freiner l'envolée des loyers.
L'encadrement des loyers est un dispositif autorisé à titre expérimental jusqu'en 2026 visant à limiter l'augmentation du loyer lors de la mise en location d'un logement avec un bail d'habitation dans les "zones tendues". A ce jour, cette mesure est appliquée de 28 agglomérations de France, dont Paris, Bordeaux, Lille, villes marquées par un déséquilibre entre l'offre et la demande de logements et une hausse des prix de l'immobilier.

## 2. Objectif du projet <a name="objectif">
L'objectif de ce projet Python vise alors à déterminer les effets quantitatifs de l'encadrement de loyer sur le marché immobilier. Nous avons décidé de ne pas nous pencher sur l'effet de la loi sur le loyer et l'offre locative mais davantage sur l'évolution des prix d'achat, des prix au m² et de la variation du nombre de transactions effectuées dans les zones concernées.

Nous avons alors choisi de nous focaliser sur 2 zones pour comparer l'évolution de ces variables. La première correspond au cluster ouest de Paris,  en comparant l'évolution des tendances entre Paris 16 et Paris 17 où l'encadrement est effectif depuis le 1er juillet 2019 et les villes environnantes où il ne s'applique pas à savoir, Levallois-Perret,Boulogne-Billancourt, Clichy et Neuilly sur Seine. On réalise également cette comparaison  au Sud de Paris sur les arrondissements de Paris 13, Paris 14 et Paris 15 avec  Issy les Moulineaux, Malakoff, Montrouge ou encore Vanves.

## 3. Modélisation  <a name="modélisation">

Pour  nous avons utilisé un modèle de doubles  différences (difference in difference) qui permet donc d'évaluer l'impact de l'encadrement des loyers, grâce à la constitution d'un groupé traité bénéficiant de la politique (Paris 16, 17) et d'un groupe témoin/ de contrôle n'en bénéficiant pas (Levallois-Perret,Boulogne-Billancourt, Clichy et Neuilly sur Seine par exemple). On observe alors l'évolution de la variable dépendante à savoir le prix d'achat au m² avant et après la mise en place de l'encadrement des loyers en contrôlant à partir de variables de contrôle reprenant des caractéristiques socio-économiques. La mesure de l'effet de la politique repose alors exclusivement sur la variation au cours du temps de la variable de résultat entre les dates choisies.
On vise alors à mesure l'inflexion dans l'écart entre les 2 groupes, qui peut alors être interpéter comme l'effet moyen de la politique sur la variable de résultat.
<img src="https://miro.medium.com/v2/resize:fit:1400/1*4e97BPvG0PTnWckdMw08-w.png" alt="Difference-in-Differences. Learn another method to determine… | by Figarri  Keisha | Bukalapak Data | Medium"/>

## 4. Sources des données <a name="sources">

Nous nous sommes appuyées sur 2 bases de données : 
- L'API DVF (Demande de Valeurs Foncières).
    Ces données disponibles en open data depuis 2019 permettent de connaître les transactions immobilières intervenues au cours des 5 années en France métropolitaine et les DOM-TOM. Les données contenues sont issues d'actes notariés et d'informations cadastrales et fournissent des informations sur le type, la géographique, le prix de différentes transactions immobilières.

https://www.data.gouv.fr/fr/dataservices/api-donnees-foncieres/
https://datafoncier.cerema.fr/donnees/autres-donnees-foncieres/dvfplus-open-data

Documentation technique de cette API : 
https://apidf-preprod.cerema.fr/swagger/#/DVF%2B%20(acc%C3%A8s%20libre)/dvf_opendata_geomutations_list


Pour retrouver ce que désigne une variable, chercher dans la barre de recherche du site ci-dessous (exemple pour sterr ci-dessous)
https://doc-datafoncier.cerema.fr/doc/dv3f/mutation/sterr

Parler des difficultés liées aux nombreux changements de gestionnaires des données (comprendre et expliquer les liens entre data.gouv.fr, api.gouv.fr et le cerema ; les différentes bases de données entre DVF, DVF+ et DV3F, les restructions d'accès selon l'utilisateur et l'absence de documentation pour la partie en pure open data)

- Les données carroyées filosofi mises à disposition par l'INSEE fournissent des informations sur les caractéristiques socio-démographiques de la population  par IRIS d'habitat (population entre 1800 et 5000 habitants généralement).
Ces données nous ont été très utiles car de nombreuses variables de cette base (A CITER) ont été utilisées comme variables de contrôle dans le modèle difference-in-difference.
Pour se faire, nous avons donc fusionné  les données DVF avec les données INSEE dans un même dataframe allant jusqu'à 2021.

## 4. Présentation du dépôt Git <a name="presentation">

Notre projet est essentiellement localisé dans le notebook main.ipynb dans lequel il suffit d'exécuter les cellules du notebook.

Le dossier data.ipynb contient une copie locale des données tirées de nos sources : d'une part les données  dvf avec les clusters Ouest et Sud de Paris et d'autre part les données Filosofi de l'INSEE entre 2014 et 2021 au format csv. 

## 5. Licence <a name="licence">


