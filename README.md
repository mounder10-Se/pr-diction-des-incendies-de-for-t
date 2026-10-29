# 🌲 Prédiction des Incendies de Forêt (*Predict the Forest Fires*)

Ce dépôt GitHub contient un projet complet d'apprentissage automatique (*Machine Learning*) axé sur la prédiction de la surface brûlée par les feux de forêt dans la région nord-est du Portugal, basé sur des variables météorologiques et environnementales.

---

## 📋 À propos du projet
Ce projet résout un problème de régression complexe confronté à des valeurs aberrantes (*outliers*) prononcées. Les données proviennent initialement du dépôt **UCI Machine Learning** (*Forest Fires Data Set*). 

L'objectif est d'analyser l'impact de différents facteurs climatiques et temporels pour prédire avec précision la superficie détruite (`area`) et de comparer plusieurs algorithmes de régression.

---

## 📊 Jeu de données (`forestfires.csv`)
Le jeu de données contient 517 lignes et 13 colonnes, comprenant :
* **`X`, `Y`** : Coordonnées spatiales au sein de la grille du parc de Montesinho.
* **`month`, `day`** : Mois de l'année et jour de la semaine.
* **`FFMC`, `DMC`, `DC`, `ISI`** : Indices météorologiques du système FWI (*Fire Weather Index*).
* **`temp`** : Température en degrés Celsius.
* **`RH`** : Humidité relative en %.
* **`wind`** : Vitesse du vent en km/h.
* **`rain`** : Précipitations extérieures en mm/m².
* **`area`** : Surface de la forêt brûlée en hectares (variable cible).

---

## ⚙️ Méthodologie et Prétraitement
1. **Transformation de la variable cible :** Application d'une transformation logarithmique $\ln(x + 1)$ sur la variable `area` pour réduire l'asymétrie de la distribution.
2. **Gestion des variables catégorielles :** Conversion des variables textuelles en valeurs numériques à l'aide de variables factices (*dummies* via `get_dummies()`) et d'encodeurs d'étiquettes (*Label Encoder*).
3. **Séparation des données :** Division rigoureuse du dataset en ensembles d'entraînement (*train*) et de test (*test*).

---

## 🤖 Modèles et Résultats
Trois approches ont été comparées :
* **Régression Linéaire**
* **Réseau Neuronal**
* **Régresseur Forestier Aléatoire (*Random Forest Regressor* - RFR)**

> **Résultat clé :** Le **Random Forest Regressor** (optimisé à l'aide de `GridSearchCV` pour la validation croisée) s'est avéré être le meilleur modèle, atteignant une valeur **RMSE de 0,628**. L'analyse des courbes d'erreur de régression (REC) a démontré qu'il prédit plus efficacement les petits incendies avec une marge d'erreur réduite.

---

## 📁 Structure du Dépôt
```text
pr-diction-des-incendies-de-for-t/
│
└───Predict the Forest Fires/
    │   ForestFire.ipynb    # Jupyter Notebook contenant l'EDA et les modèles
    │   forestfires.csv     # Jeu de données source
