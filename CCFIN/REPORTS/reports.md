````markdown
# Étude sur la qualité de l'air - Dataset UCI (ID: 360)

## 📋 Informations générales

**DOI:** 10.24432/C59K5F  
**Créateur:** Saverio Vito  
**Date de don:** 22 mars 2016  
**Publication associée:** De Vito et al., Sensors and Actuators B: Chemical, Vol. 129,2, 2008  
**Licence:** Creative Commons Attribution 4.0 International (CC BY 4.0)

## 🎯 Objectif de l'étude

Cette étude vise à enregistrer et analyser les réponses d'un dispositif multicapteur de gaz déployé sur le terrain dans une ville italienne. Les réponses moyennes horaires sont enregistrées parallèlement aux concentrations de gaz de référence provenant d'un analyseur certifié.

## 📍 Zone géographique et contexte

- **Lieu:** Ville italienne (nom non spécifié)
- **Emplacement précis:** Zone significativement polluée, au niveau de la route
- **Type d'environnement:** Urbain, exposition directe à la pollution routière

## ⏰ Période de collecte

- **Début:** Mars 2004
- **Fin:** Février 2005
- **Durée totale:** 1 an (12 mois consécutifs)
- **Fréquence d'enregistrement:** Moyennes horaires
- **Particularité:** Il s'agit du plus long enregistrement librement disponible de réponses de capteurs chimiques de qualité de l'air déployés sur le terrain

## 🔬 Dispositif technique

### Capteurs utilisés
Le dispositif contient un réseau de **5 capteurs chimiques à oxyde métallique** :

1. **PT08.S1** (oxyde d'étain) - ciblant le CO
2. **PT08.S2** (dioxyde de titane) - ciblant les NMHC
3. **PT08.S3** (oxyde de tungstène) - ciblant les NOx
4. **PT08.S4** (oxyde de tungstène) - ciblant le NO2
5. **PT08.S5** (oxyde d'indium) - ciblant l'O3

### Analyseur de référence co-localisé
Un analyseur certifié a fourni les concentrations réelles (Ground Truth) pour validation.

## 📊 Données collectées

### Caractéristiques du dataset
- **Nombre d'instances:** 9 358 enregistrements horaires
- **Nombre de variables:** 15
- **Type de données:** Multivarié, séries temporelles
- **Valeurs manquantes:** Oui (marquées avec la valeur -200)

### Variables mesurées

#### Polluants (concentrations réelles de référence)
1. **CO(GT)** - Monoxyde de carbone (mg/m³)
2. **NMHC(GT)** - Hydrocarbures non méthaniques totaux (µg/m³)
3. **C6H6(GT)** - Benzène (µg/m³)
4. **NOx(GT)** - Oxydes d'azote totaux (ppb)
5. **NO2(GT)** - Dioxyde d'azote (µg/m³)

#### Réponses des capteurs
- PT08.S1 à PT08.S5 (réponses moyennes horaires de chaque capteur)

#### Variables environnementales
- **Température** (°C)
- **Humidité relative** (%)
- **Humidité absolue** (AH)

#### Variables temporelles
- **Date** (JJ/MM/AAAA)
- **Heure** (HH.MM.SS)

## ⚠️ Défis et particularités

### Problèmes identifiés
L'étude a mis en évidence plusieurs défis techniques importants :

1. **Sensibilités croisées:** Les capteurs réagissent à plusieurs polluants, pas uniquement à leur cible nominale
2. **Dérive conceptuelle:** Changements dans les relations entre les entrées et sorties au fil du temps
3. **Dérive des capteurs:** Dégradation des performances des capteurs physiques pendant la période de déploiement

Ces phénomènes affectent les capacités d'estimation des concentrations des capteurs, comme décrit dans la publication de De Vito et al. (2008).

## 🎓 Utilisation du dataset

### Tâches associées
- **Régression:** Prédiction des concentrations de polluants
- **Calibration de capteurs:** Correction des dérives et sensibilités croisées
- **Surveillance environnementale:** Modélisation de la qualité de l'air urbain

### Restrictions d'usage
- ✅ **Autorisé:** Utilisation exclusivement à des fins de recherche
- ❌ **Interdit:** Toute utilisation commerciale

### Format des fichiers
- **AirQualityUCI.csv** (766.7 KB)
- **AirQualityUCI.xlsx** (1.2 MB)

## 📚 Citations et publications

### Citation principale
````
Vito, S. (2008). Air Quality [Dataset]. UCI Machine Learning Repository. 
https://doi.org/10.24432/C59K5F
````

### Article introductif
"On field calibration of an electronic nose for benzene estimation in an urban pollution monitoring scenario"  
Par S. D. Vito, E. Massera, M. Piga, L. Martinotto, G. Francia (2008)  
Publié dans *Sensors and Actuators B: Chemical*

### Autres publications utilisant ce dataset
- "Boosting for Dynamical Systems" (Agarwal et al., 2019)
- "Zoom-SVD: Fast and Memory Efficient Method for Extracting Key Patterns in an Arbitrary Time Range" (Jang et al., 2018)
- "Combined modeling of sparse and dense noise for improvement of Relevance Vector Machine" (Sundin et al., 2015)

## 💡 Importance pour la recherche

Ce dataset est particulièrement précieux pour la recherche en machine learning car :

1. **Données réelles de terrain:** Reflète les conditions authentiques de surveillance environnementale
2. **Longue durée:** Une année complète d'enregistrements continus
3. **Défis réalistes:** Présence de dérives et de sensibilités croisées typiques des déploiements réels
4. **Données de référence:** Disponibilité des concentrations réelles via un analyseur certifié
5. **Librement accessible:** Sous licence ouverte pour la recherche

## 🔗 Accès au dataset

### Via UCI ML Repository
```python
from ucimlrepo import fetch_ucirepo

# Récupérer le dataset
air_quality = fetch_ucirepo(id=360)

# Données (DataFrames pandas)
X = air_quality.data.features
y = air_quality.data.targets

# Métadonnées
print(air_quality.metadata)

# Informations sur les variables
print(air_quality.variables)
```

### Téléchargement direct
Taille totale: 1.5 MB (fichiers CSV et Excel disponibles)
````
