# Data Modeling

## Projet

Market Intelligence Platform

## Version

0.1

## Objectif

Ce document présente la modélisation des données nécessaire au fonctionnement de Market Intelligence Platform.

L'objectif est de définir une structure permettant de collecter, stocker, analyser et exploiter les données provenant de plusieurs marketplaces e-commerce.

La modélisation devra être évolutive afin de permettre l'ajout de nouvelles sources de données et de nouvelles fonctionnalités.

---

# 1. Principes de modélisation

La base de données doit respecter plusieurs principes :

* éviter la duplication des données ;
* faciliter les analyses ;
* permettre l'évolution vers un Data Warehouse ;
* supporter plusieurs marketplaces ;
* préparer le calcul des indicateurs et du Market Opportunity Score.

---

# 2. Vue globale du modèle

Architecture simplifiée :

```
                    Marketplace
                         |
                         |
                      Produit
                    /    |    \
                   /     |     \
              Prix    Vendeur   Catégorie
                   \
                    \
              Historique Prix
                         |
                         |
                  Analyse Produit
                         |
                         |
             Market Opportunity Score
```

---

# 3. Entités principales

## 3.1 Marketplace

Cette table représente les différentes plateformes e-commerce analysées.

Exemples :

* Amazon
* Etsy
* Cdiscount
* Fnac
* AliExpress

### Structure

| Champ          | Description              |
| -------------- | ------------------------ |
| id_marketplace | Identifiant unique       |
| nom            | Nom de la marketplace    |
| pays           | Zone géographique        |
| url            | Adresse de la plateforme |

---

# 3.2 Produit

Cette table représente les produits analysés.

### Structure

| Champ       | Description          |
| ----------- | -------------------- |
| id_produit  | Identifiant unique   |
| nom_produit | Nom du produit       |
| categorie   | Catégorie du produit |
| marque      | Marque               |
| description | Description          |

---

# 3.3 Association Produit - Marketplace

Un même produit peut exister sur plusieurs marketplaces.

Cette table permet de gérer cette relation.

### Structure

| Champ                  | Description          |
| ---------------------- | -------------------- |
| id_produit_marketplace | Identifiant          |
| id_produit             | Produit associé      |
| id_marketplace         | Marketplace associée |
| url_produit            | Lien du produit      |
| date_collecte          | Date de récupération |

---

# 3.4 Vendeur

Cette table représente les vendeurs présents sur une marketplace.

### Structure

| Champ       | Description   |
| ----------- | ------------- |
| id_vendeur  | Identifiant   |
| nom_vendeur | Nom           |
| note        | Evaluation    |
| nombre_avis | Nombre d'avis |

---

# 3.5 Historique des prix

Cette table permet de suivre l'évolution du prix d'un produit.

Elle est essentielle pour analyser les tendances.

### Structure

| Champ                  | Description      |
| ---------------------- | ---------------- |
| id_prix                | Identifiant      |
| id_produit_marketplace | Produit concerné |
| date                   | Date de collecte |
| prix                   | Prix observé     |

---

# 3.6 Analyse Produit

Cette table stocke les indicateurs calculés.

### Structure

| Champ         | Description           |
| ------------- | --------------------- |
| id_analyse    | Identifiant           |
| id_produit    | Produit analysé       |
| date_analyse  | Date                  |
| concurrence   | Niveau de concurrence |
| tendance      | Evolution du produit  |
| marge_estimee | Marge potentielle     |

---

# 3.7 Market Opportunity Score

Cette table stocke le score d'opportunité calculé.

### Structure

| Champ             | Description            |
| ----------------- | ---------------------- |
| id_score          | Identifiant            |
| id_produit        | Produit analysé        |
| score_total       | Score sur 100          |
| score_tendance    | Sous-score tendance    |
| score_concurrence | Sous-score concurrence |
| score_marge       | Sous-score marge       |
| date_calcul       | Date du calcul         |

---

# 4. Evolution vers un Data Warehouse

Dans une version plus avancée, le modèle pourra évoluer vers une architecture analytique :

## Tables de faits

Exemples :

* Fait_Prix
* Fait_Vente
* Fait_Analyse

## Dimensions

Exemples :

* Dim_Produit
* Dim_Marketplace
* Dim_Temps
* Dim_Categorie

Cette évolution permettra une meilleure utilisation avec :

* dbt ;
* Power BI ;
* Tableau ;
* Snowflake ;
* BigQuery.

---

# 5. Questions ouvertes

Les points suivants devront être étudiés :

* Comment récupérer les données des marketplaces ?
* Quelle fréquence de collecte ?
* Quelles données sont réellement accessibles ?
* Comment mesurer la concurrence ?
* Comment calculer précisément la marge ?
* Comment améliorer le Market Opportunity Score ?
