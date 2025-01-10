# Prédictions de l'épaisseur de la banquise dans l'Arctique

Ce projet présente une analyse et des prédictions de l'épaisseur de la banquise dans une région spécifique de l'Arctique, basée sur les données du **Copernicus Climate Data Store**. Les données ont été filtrées pour une zone d'intérêt et analysées dans le but de prédire l'épaisseur moyenne de la glace pour les 10 prochaines années à l'aide de modèles ARIMA et de régression linéaire.

## Contenu

1. [Données utilisées](#données-utilisées)
2. [Structure du projet](#structure-du-projet)
3. [Prérequis](#prérequis)
4. [Instructions](#instructions)
5. [Analyse et résultats](#analyse-et-résultats)
6. [Améliorations futures](#améliorations-futures)

---

## Données utilisées

Les données proviennent du jeu de données **Satellite Sea Ice Thickness** disponible sur le [Copernicus Climate Data Store](https://cds.climate.copernicus.eu/datasets/satellite-sea-ice-thickness?tab=overview).

### Caractéristiques des données :
- **Format** : NetCDF (.nc)
- **Variables principales** :
  - `sea_ice_thickness` : Épaisseur de la glace (en mètres).
  - `lat` et `lon` : Coordonnées géographiques (latitude et longitude).
  - `xc` et `yc` : Coordonnées en projection Lambert Azimuthal Equal-Area (en km).
  - `time` : Dates des mesures.
- **Période** : 2003 à 2020 (avec des prévisions jusqu'en 2030).

---

## Structure du projet

Le projet comprend les étapes suivantes :

1. **Chargement des données** : Fusion des fichiers NetCDF pour créer un dataset unifié.
2. **Filtrage par région** :
   - Sélection d'une zone basée sur les **eastings** (x-coordinate) et **northings** (y-coordinate).
   - Zone ciblée : Eastings entre **1000 km** et **3000 km**, Northings entre **-3000 km** et **-1000 km**.
3. **Analyse exploratoire** :
   - Moyenne temporelle de l'épaisseur de la glace.
   - Visualisation des variations spatiales et temporelles.
4. **Prédictions** :
   - Régression linéaire : Estimation simple basée sur la tendance historique.
   - Modèle ARIMA : Prédiction des 10 prochaines années.
5. **Visualisation** :
   - Graphiques des données historiques et des prédictions.

---

## Prérequis

### Logiciels et bibliothèques

- **Python 3.8+**
- Bibliothèques Python :
  - `xarray` : Manipulation des fichiers NetCDF.
  - `matplotlib` : Visualisation des données.
  - `pandas` : Manipulation des données tabulaires.
  - `numpy` : Calcul scientifique.
  - `statsmodels` : Modélisation ARIMA.
  - `scikit-learn` : Régression linéaire et évaluation du modèle.

### Installation des dépendances

Installe les dépendances avec la commande suivante :

```bash
pip install xarray matplotlib pandas numpy statsmodels scikit-learn
```

---

## Instructions

### 1. Téléchargement des données

Les fichiers NetCDF doivent être téléchargés depuis le [site du Climate Data Store](https://cds.climate.copernicus.eu/). 

### 2. Exécution du script principal

Les données doivent être placées dans un dossier ice_2003_2020_avril à la racine du projet.

### 3. Visualisation des résultats

Les résultats incluent :
- Un graphique montrant l'évolution historique de l'épaisseur de la glace.
- Les prévisions pour les 10 prochaines années superposées aux données historiques.

---

## Analyse et résultats

### Points clés des résultats :
1. **Variation temporelle** : Les données montrent une tendance générale de diminution de l'épaisseur de la glace, avec des variations saisonnières.
2. **Prédictions ARIMA** : Le modèle ARIMA prévoit une épaisseur moyenne de glace d'environ **0.48 m à 0.61 m** pour les 10 prochaines années.
3. **Résultats du modèle** : Une erreur quadratique moyenne (MSE) de **0.007** indique une précision raisonnable pour le modèle ARIMA sur les données historiques.

### Visualisations :
- Évolution historique de l'épaisseur de la glace dans la région ciblée.
- Prédictions pour les prochaines années avec les incertitudes associées.

---

## Améliorations futures

1. **Affinage de la région** :
   - Tester des zones géographiques différentes pour évaluer la variabilité des résultats.
   - Convertir les coordonnées projetées (xc, yc) en latitudes et longitudes pour faciliter l'interprétation.

2. **Amélioration des modèles** :
   - Intégrer des modèles plus complexes (par exemple, Random Forest ou XGBoost).
   - Ajouter des variables explicatives (température de surface, couverture nuageuse, etc.).

3. **Résolution temporelle** :
   - Utiliser des données journalières pour des prédictions plus précises.

4. **Visualisation interactive** :
   - Implémenter des visualisations interactives (par exemple, avec Plotly ou Dash) pour explorer les résultats.



