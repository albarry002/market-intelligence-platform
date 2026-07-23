# Product Backlog

## Projet

Market Intelligence Platform

## Version

0.1

---

# Organisation du backlog

Les tâches sont organisées par priorité :

* P0 : indispensable pour le MVP
* P1 : important mais non bloquant
* P2 : amélioration future

---

# Epic 1 — Fondations du projet

## P0 — Mettre en place la structure GitHub

Objectif :
Créer une organisation professionnelle du projet.

Tâches :

* créer l'arborescence du projet ;
* organiser les dossiers ;
* définir les conventions de nommage ;
* mettre en place les branches Git.

---

## P0 — Documentation initiale

Tâches :

* écrire la vision du projet ;
* écrire le storytelling ;
* écrire le PRD ;
* documenter les décisions importantes.

---

# Epic 2 — Collecte des données

## P0 — Identifier les sources de données

Objectif :
Définir quelles marketplaces seront étudiées.

Premières sources possibles :

* Amazon ;
* Etsy ;
* Cdiscount ;
* Fnac ;
* AliExpress.

---

## P0 — Créer un premier jeu de données

Objectif :
Disposer de données permettant de développer le produit.

Données possibles :

* nom du produit ;
* catégorie ;
* prix ;
* nombre de vendeurs ;
* avis ;
* date de collecte.

---

# Epic 3 — Stockage des données

## P0 — Concevoir la base de données

Objectif :

Créer une première architecture de stockage.

Technologies envisagées :

* PostgreSQL.

Travaux :

* définir les tables ;
* créer le schéma ;
* documenter le modèle.

---

# Epic 4 — Transformation des données

## P1 — Mettre en place les transformations analytiques

Objectif :

Préparer les données pour l'analyse.

Technologies envisagées :

* SQL ;
* dbt.

Travaux :

* nettoyage ;
* création des modèles analytiques ;
* tests de qualité.

---

# Epic 5 — Analyse et visualisation

## P0 — Construire le premier dashboard

Objectif :

Afficher les premiers indicateurs.

Technologies envisagées :

* Streamlit ;
* Power BI.

Indicateurs :

* évolution des prix ;
* concurrence ;
* tendances ;
* comparaison de produits.

---

# Epic 6 — Market Opportunity Score

## P1 — Première version du score

Objectif :

Créer un indicateur permettant d'évaluer une opportunité produit.

Travaux :

* définir les critères ;
* créer une première formule ;
* tester la pertinence.

---

# Epic 7 — Industrialisation

## P2 — Automatisation

Technologies envisagées :

* Airflow ;
* Docker ;
* GitHub Actions.

Objectifs :

* automatiser les pipelines ;
* tester automatiquement ;
* améliorer la fiabilité.

---

# MVP cible — Septembre 2026

À la fin du MVP, la plateforme devra permettre :

✅ récupérer des données produits
✅ stocker les données
✅ analyser un produit
✅ afficher un dashboard
✅ comparer plusieurs opportunités
✅ produire un premier score d'opportunité
