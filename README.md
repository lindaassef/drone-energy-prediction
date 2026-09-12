# Prédiction de la consommation énergétique d'un drone UAV

## Contexte
Projet académique de Machine Learning réalisé à l'ISAE-SUPMECA.

## Objectif
Analyser et modéliser la consommation énergétique d'un drone quadricoptère à partir de données réelles de vol (209 vols, ~258 000 mesures à 5 Hz), afin de prédire la puissance consommée en fonction des paramètres de vol (vitesse, altitude, charge transportée, vent, orientation, accélérations...).

## Démarche

**1. Préparation des données**
- Vérification des valeurs manquantes (aucune détectée)
- Création de la variable cible `puissance` = tension × courant de la batterie
- Nettoyage de la colonne `altitude` (conversion des intervalles en valeurs moyennes)
- Feature engineering : fusion des composantes de vitesse (`velocity_x/y/z`) en une norme unique `velocity`
- Suppression des variables non informatives (`route`, `flight`, `time`) pour limiter le risque de surapprentissage
- Séparation train/test (70/30) et normalisation (StandardScaler)

**2. Modélisation**
Cinq familles de modèles testées et comparées sur RMSE, MAE et R² : Régression linéaire,Régression polynomiale (deg. 4) ,SVR (optimisé GridSearchCV),Réseaux de neurones (MLP), Random Forest

## Résultat
Le **Random Forest** est le modèle retenu, avec le RMSE le plus faible et un R² de 0.967 (confirmé par validation croisée à 5 folds, R² moyen = 0.965). Il capture bien les relations non linéaires entre les paramètres de vol et la consommation, tout en restant robuste au bruit.

## Outils
Python, Pandas, NumPy, Matplotlib, Scikit-learn (LinearRegression, PolynomialFeatures, MLPRegressor, RandomForestRegressor, SVR, GridSearchCV)

## Livrables
📊 [Présentation du projet](./presentation-projet.pptx)
📄 [Rapport détaillé (PDF)](./projet_DATA.pdf)
