# FlightRadar24

# Sujet


Créer un pipeline ETL (Extract, Transform, Load) permettant de traiter les données de l'API [flightradar24](https://www.flightradar24.com/), qui répertorie l'ensemble des vols aériens, aéroports, compagnies aériennes mondiales.

> En python, cette librairie: https://github.com/JeanExtreme002/FlightRadarAPI facilite l'utilisation de l'API.

## Résultats

Ce pipeline doit permettre de fournir les indicateurs suivants:
1. La compagnie avec le + de vols en cours
2. Pour chaque continent, la compagnie avec le + de vols régionaux actifs (continent d'origine == continent de destination)
3. Le vol en cours avec le trajet le plus long
4. Pour chaque continent, la longueur de vol moyenne
5. L'entreprise constructeur d'avions avec le plus de vols actifs
6. Pour chaque continent, le modèle d'avion le plus utilisé

## Industrialisation

Ce kata est orienté **industrialisation**. Le pipeline ETL doit être pensé comme un job se faisant éxécuter à échéance régulière (ex: toutes les 2 heures).

Le job doit donc être
* **fault-tolerant**: Un corner-case pas couvert ou une donnée corrompue ne doivent pas causer l'arret du job.
* **systématique**: conserver les données & résultats dans un mécanisme de stockage, en adoptant une nomencalture adaptée permettant aux _data analyst_ en aval de retrouver les valeurs recherchées pour un couple `(Date, Heure)` donné.
* **ré-exécutable**: le data analyst qui vous corrigera doit être en mesure de ré-exécuter les jobs localement et constater les même résultats.

![flightradarimage](media-assets/flightradar.png)

# Note d'intention

## ⚠️ MVP ⚠️

 

> Le kata laisse volontairement beaucoup de liberté. Il y a une grande marge de progression entre un “MVP” et une implémentation “parfaite”. Au candidat de choisir sur quelles exigences mettre le focus dans son rendu.

> Le rendu MVP implémente au moins 4 des questions de l'énoncé, assorti d'un Readme expliquant la démarche choisie

___

## Contexte


Un data engineer doit être capable de concevoir un pipeline de données pour gérer un flux important et en tirer des informations pertinentes. 

 

En tant que data engineer, il est important de pouvoir **explorer & comprendre le dataset qu’on manipule** pour proposer les Vues adaptées au différents use-cases, et effectuer le data-cleaning nécessaire. 

https://www.flightradar24.com/ est une API fournissant des informations **en temps réel** sur le traffic aérien mondial. De ce fait, les informations qu'elle renvoie changent en parmanence. Pour en tirer des informations utiles, son traitement doit donc **doit être répété régulièrement**. Pour des raisons d'efficacité, on cherche donc à transformer ce pipeline ETL en **un job ne requérant pas d'intervention humaine.**


___

## Specification [RFC2119](https://microformats.org/wiki/rfc-2119-fr) du kata


