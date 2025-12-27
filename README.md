# Analyse et Prévision de Séries Temporelles

**Projet d'Économétrie Appliquée**

---

## Présentation du projet

Ce projet porte sur l'étude statistique et la prévision de séries chronologiques. L'objectif est de modéliser l'évolution de l'indice de production industrielle dans le secteur pharmaceutique en France en utilisant les méthodologies de Box-Jenkins.

## Approche Méthodologique

Le projet suit une démarche rigoureuse en plusieurs étapes :

1. **Analyse Exploratoire** : Décomposition de la série en composantes déterministes (tendance et saisonnalité) et résidus.
2. **Stationnarisation** : 
   - Application de transformations appropriées pour stabiliser la variance si nécessaire.
   - Tests de racine unitaire (**Augmented Dickey-Fuller**) pour valider la stationnarité après différenciation.
3. **Identification et Estimation** :
   - Analyse des fonctions d'autocorrélation (**ACF**) et d'autocorrélation partielle (**PACF**).
   - Sélection du modèle optimal parmi plusieurs candidats (ARIMA, SARIMA).
4. **Validation et Prévision** :
   - Test de blancheur des résidus (**Ljung-Box**).
   - Prévision à l'horizon $h$ avec calcul des intervalles de confiance.

## Données

### Dataset (`dataset.csv`)

- **Secteur** : Industrie pharmaceutique (NAF rév. 2, niveau A38, poste CF)
- **Indicateur** : Indice CVS-CJO de la production industrielle (base 100 en 2015)
- **Période** : Données mensuelles de janvier 2010 à mars 2020 (123 observations)
- **Source** : INSEE - Banque de données (ID: 010537926)
- **Format** : CSV avec séparateur point-virgule (`;`)
- **Qualité** : Données définitives (code A)

### Caractéristiques

- **Fréquence** : Mensuelle
- **Corrections appliquées** : CVS (Corrigé des Variations Saisonnières) et CJO (Corrigé des Jours Ouvrables)
- **Tendance observée** : Croissance générale de la production sur la période

## Outils et Environnement

- **Langage** : R ou Python
- **Bibliothèques recommandées** :
  - **R** : `forecast`, `tseries`, `ggplot2`, `stats`
  - **Python** : `pandas`, `numpy`, `matplotlib`, `statsmodels`, `prophet`
- **Concepts clés** : Modèles SARIMA, Tests de blancheur, Critères d'information (AIC/BIC)

## Structure du Projet

```
Serie Temp/
├── dataset.csv              # Données de production industrielle pharmaceutique
├── Series_temporelles.pdf   # Documentation et démonstrations mathématiques
└── README.md                # Ce fichier
```

## Résultats et Validation

### Décomposition de la série

L'analyse exploratoire révèle une décomposition claire de la série temporelle en trois composantes :
- **Tendance** : Évolution à long terme de la production pharmaceutique
- **Saisonnalité** : Variations cycliques mensuelles récurrentes
- **Résidus** : Composante aléatoire restante après extraction des composantes déterministes

### Modèle final

Le modèle SARIMA sélectionné capture efficacement les caractéristiques de la série :

$$SARIMA(p,d,q)(P,D,Q)_s$$

où les paramètres optimaux sont déterminés par minimisation des critères d'information (AIC/BIC) et validation croisée.

### Diagnostic des résidus

La validation du modèle repose sur l'analyse approfondie des résidus :

- **Test de blancheur (Ljung-Box)** : Les résidus se comportent comme un **bruit blanc**, confirmant l'absence d'autocorrélation résiduelle
- **Normalité des résidus** : Distribution des résidus conforme aux hypothèses du modèle
- **Homoscédasticité** : Variance constante des résidus dans le temps

Ces diagnostics garantissent la validité statistique du modèle et la fiabilité des prévisions.

### Prévisions

Le modèle final permet de capturer avec précision les tendances et saisonnalités de la production pharmaceutique et de fournir des prévisions robustes avec intervalles de confiance pour les périodes futures.

---

*Consultez le fichier `Series_temporelles.pdf` pour les démonstrations mathématiques complètes, les graphiques de décomposition, les diagnostics des résidus et les résultats détaillés.*

