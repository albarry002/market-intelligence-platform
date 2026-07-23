Décision d'architecture #001

Sujet : Support multi-marketplaces

Décision :
La plateforme sera conçue pour supporter plusieurs marketplaces.

Sources envisagées :

Amazon
Etsy
Cdiscount
Fnac
AliExpress

Justification :

Une architecture multi-sources permettra de construire une vision globale du marché e-commerce et évitera de dépendre d'une seule plateforme.

Approche :

L'intégration des marketplaces sera progressive.

Chaque marketplace sera ajoutée comme une nouvelle source de données indépendante.

# Architecture du système

## Projet

Market Intelligence Platform

## Version

0.1

## Date

23 juillet 2026

---

# 1. Introduction

Market Intelligence Platform repose sur une architecture Data permettant de collecter, stocker, transformer, analyser et visualiser des données provenant de plusieurs marketplaces e-commerce.

L'objectif est de construire progressivement une plateforme capable d'aider les vendeurs à prendre des décisions basées sur les données.

L'architecture doit être :

* évolutive ;
* maintenable ;
* documentée ;
* capable d'intégrer plusieurs sources de données ;
* adaptée à une évolution vers une solution professionnelle.

---

# 2. Vision globale de l'architecture

L'architecture générale suit une approche Data Platform :

```
Sources e-commerce
        |
        ↓
Data Collection Layer
        |
        ↓
Raw Data Storage
        |
        ↓
Data Warehouse
        |
        ↓
Transformation Layer
        |
        ↓
Analytics Layer
        |
        ↓
Visualization Layer
```

Chaque couche possède un rôle précis dans le traitement de la donnée.

---

# 3. Sources de données

## Objectif

Permettre l'analyse de plusieurs marketplaces afin d'obtenir une vision globale du marché.

## Marketplaces envisagées

* Amazon
* Etsy
* Cdiscount
* Fnac
* AliExpress

## Approche

L'architecture sera conçue pour supporter plusieurs sources indépendantes.

Chaque marketplace sera considérée comme un connecteur de données séparé.

Exemple :

```
src/

 └── ingestion/

      ├── amazon/

      ├── etsy/

      ├── cdiscount/

      ├── fnac/

      └── aliexpress/
```

Cette organisation permettra d'ajouter de nouvelles sources sans modifier toute l'architecture.

---

# 4. Couche d'ingestion des données

## Objectif

Collecter automatiquement les informations provenant des marketplaces.

## Technologies envisagées

* Python
* APIs lorsque disponibles
* Scraping lorsque nécessaire
* Fichiers CSV pour les premiers tests

## Données collectées possibles

* nom du produit ;
* catégorie ;
* prix ;
* vendeur ;
* nombre d'avis ;
* note ;
* disponibilité ;
* historique des prix ;
* date de collecte.

---

# 5. Stockage des données

L'architecture utilise plusieurs niveaux de stockage.

---

## 5.1 Raw Data Storage

Objectif :

Conserver les données originales collectées avant transformation.

Exemples de formats :

* CSV
* JSON
* Parquet

Structure envisagée :

```
data/

 ├── raw/

 └── processed/
```

Cette couche permet de garder une trace des données sources.

---

## 5.2 Data Warehouse

Objectif :

Stocker des données structurées adaptées à l'analyse.

Technologie initiale :

* PostgreSQL

Évolution possible :

* Snowflake
* Google BigQuery

Le Data Warehouse permettra de construire des modèles analytiques fiables.

---

# 6. Modélisation des données

Objectif :

Organiser les données afin de faciliter les analyses.

Les modèles pourront évoluer vers une architecture analytique comprenant :

* tables de faits ;
* dimensions ;
* indicateurs calculés.

Exemple :

```
Produits
    |
    |
Prix historiques
    |
    |
Vendeurs
    |
    |
Marketplace
```

---

# 7. Couche de transformation (Analytics Engineering)

## Objectif

Transformer les données brutes en données exploitables.

Technologie envisagée :

* dbt

Les transformations permettront :

* nettoyage des données ;
* normalisation ;
* création des indicateurs ;
* préparation des analyses ;
* calcul des métriques nécessaires au score d'opportunité.

---

# 8. Couche Analytics

Cette couche représente l'intelligence du produit.

Elle contient :

* KPI ;
* analyses ;
* tendances ;
* comparaisons ;
* Market Opportunity Score.

Elle répond à la question :

> Que disent les données ?

---

# 9. Market Opportunity Score

Le Market Opportunity Score est un indicateur permettant d'évaluer le potentiel commercial d'un produit.

Objectif :

Transformer plusieurs informations du marché en une analyse simple permettant d'aider à la décision.

Critères envisagés :

* tendance du produit ;
* évolution du prix ;
* concurrence ;
* nombre de vendeurs ;
* potentiel de marge ;
* stabilité du marché.

Évolution prévue :

## Version initiale

Score basé sur des règles définies.

## Versions futures

Amélioration possible avec :

* statistiques ;
* modèles prédictifs ;
* Machine Learning.

---

# 10. Couche de visualisation

## Objectif

Présenter les analyses de manière claire aux utilisateurs.

## Première version

Technologies :

* Streamlit

## Évolution

Technologies possibles :

* Power BI
* Tableau

## Dashboards prévus

### Dashboard produit

Afficher :

* prix ;
* évolution ;
* concurrence ;
* tendances ;
* score.

### Dashboard comparaison

Comparer plusieurs produits.

### Dashboard marché

Analyser les tendances globales.

---

# 11. Orchestration des traitements

## Objectif

Automatiser les différents pipelines.

Technologie envisagée :

* Apache Airflow

Automatisations possibles :

* collecte quotidienne ;
* transformation automatique ;
* mise à jour des indicateurs ;
* actualisation des dashboards.

---

# 12. Industrialisation et DevOps

Objectif :

Rendre le projet professionnel et maintenable.

Technologies envisagées :

## Conteneurisation

* Docker

## Versioning

* Git
* GitHub

## Intégration continue

* GitHub Actions

Objectifs :

* tester automatiquement le code ;
* vérifier la qualité ;
* automatiser les déploiements.

---

# 13. Évolution de l'architecture

L'architecture évoluera avec les versions du produit.

## Version initiale

Objectif :

Créer une première plateforme fonctionnelle.

Architecture :

Python → PostgreSQL → Streamlit

---

## Version intermédiaire

Ajout :

* dbt ;
* Airflow ;
* Docker.

---

## Version avancée

Ajout possible :

* Cloud ;
* Snowflake ou BigQuery ;
* CI/CD complet ;
* Machine Learning ;
* API publique.

---

# 14. Principes architecturaux

Le projet suit plusieurs principes :

## Construire progressivement

Chaque technologie sera ajoutée lorsqu'elle répond à un besoin réel.

## Séparer les responsabilités

Chaque couche possède un rôle précis.

## Documenter les décisions

Les choix techniques seront expliqués.

## Favoriser l'évolution

L'architecture doit permettre d'ajouter de nouvelles marketplaces et fonctionnalités.

