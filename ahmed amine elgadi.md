# Rapport d'Analyse Approfondie du PIB
## Comparaison Internationale Multi-Pays

ahmed amine elgadi
![WhatsApp Image 2024-04-22 à 17 00 00_56bf9be3](https://github.com/user-attachments/assets/3f55ffb9-610a-496f-a563-7206dd919e95)


## 1. Introduction et Cadrage de l'Étude

### 1.1 Objectif de l'analyse

L'objectif principal de cette analyse est d'examiner l'évolution et la comparaison du Produit Intérieur Brut (PIB) de plusieurs économies majeures sur une période récente. Cette étude vise à :

- Comparer les performances économiques de différents pays développés et émergents
- Identifier les tendances de croissance économique
- Analyser les disparités de développement entre nations
- Fournir une base analytique pour comprendre la dynamique économique mondiale

### 1.2 Méthodologie générale employée

Cette analyse adopte une approche quantitative basée sur :

1. **Collecte de données** : Extraction de données macroéconomiques officielles
2. **Traitement statistique** : Nettoyage, transformation et calculs descriptifs
3. **Analyse comparative** : Comparaisons inter-pays et temporelles
4. **Visualisation** : Représentations graphiques multiples pour faciliter l'interprétation
5. **Interprétation** : Analyse économique contextuelle des résultats

### 1.3 Pays sélectionnés et période d'analyse

**Pays analysés :**
- États-Unis (économie développée, leader mondial)
- Chine (économie émergente, croissance rapide)
- Allemagne (économie européenne majeure)
- Japon (économie développée asiatique)
- Inde (économie émergente à forte croissance)
- France (économie développée européenne)

**Période d'analyse :** 2015-2023 (9 années)

Cette sélection représente un échantillon diversifié d'économies mondiales, permettant des comparaisons significatives entre modèles de développement.

### 1.4 Questions de recherche principales

1. Quelles sont les différences de taille économique entre ces pays ?
2. Comment le PIB a-t-il évolué dans le temps pour chaque pays ?
3. Quels pays affichent les taux de croissance les plus élevés ?
4. Comment se compare le PIB par habitant entre ces nations ?
5. Existe-t-il des corrélations entre les performances économiques ?

---

## 2. Description des Données

### 2.1 Source des données

**Source principale :** Banque mondiale - Indicateurs de développement mondial (World Development Indicators)

**Sources complémentaires :**
- Fonds Monétaire International (FMI) - World Economic Outlook
- OCDE - Base de données statistiques

Ces sources sont reconnues internationalement pour leur fiabilité et leur méthodologie standardisée.

### 2.2 Variables analysées

| Variable | Description | Unité |
|----------|-------------|-------|
| PIB nominal | Produit Intérieur Brut total | Milliards USD |
| PIB par habitant | PIB divisé par la population | USD/habitant |
| Taux de croissance | Variation annuelle du PIB | % |
| Population | Nombre d'habitants | Millions |

### 2.3 Période couverte

**Début :** 2015  
**Fin :** 2023  
**Fréquence :** Annuelle  
**Nombre d'observations :** 54 (9 années × 6 pays)

### 2.4 Qualité et limitations des données

**Points forts :**
- Données officielles et vérifiées
- Méthodologie standardisée internationale
- Mise à jour régulière

**Limitations :**
- Les données de 2023 peuvent être provisoires
- Les comparaisons sont en USD courants (impact des taux de change)
- Ne reflètent pas la parité de pouvoir d'achat (PPA)
- Ne capturent pas l'économie informelle
- Agrégats nationaux masquant les inégalités internes

### 2.5 Tableau récapitulatif des données (2023)

| Pays | PIB (Mds USD) | PIB/hab (USD) | Croissance (%) | Population (M) |
|------|---------------|---------------|----------------|----------------|
| États-Unis | 27 360 | 82 034 | 2.5 | 334 |
| Chine | 17 963 | 12 720 | 5.2 | 1 412 |
| Allemagne | 4 456 | 53 571 | -0.3 | 83.2 |
| Japon | 4 231 | 33 815 | 1.9 | 125 |
| Inde | 3 737 | 2 612 | 7.2 | 1 430 |
| France | 3 030 | 45 202 | 0.9 | 67 |

---

## 3. Code d'Analyse - Implémentation Technique

### 3.1 Importation des bibliothèques

**Explication préalable :**  
Nous commençons par importer les bibliothèques Python essentielles pour l'analyse de données et la visualisation. Chaque bibliothèque a un rôle spécifique dans notre pipeline analytique.

```python
# Bibliothèque pour la manipulation et l'analyse de données tabulaires
import pandas as pd

# Bibliothèque pour les calculs numériques et opérations matricielles
import numpy as np

# Bibliothèque de base pour la création de graphiques
import matplotlib.pyplot as plt

# Bibliothèque avancée pour des visualisations statistiques élégantes
import seaborn as sns

# Module pour formater les montants en devise
from matplotlib.ticker import FuncFormatter

# Configuration de l'affichage des graphiques
# 'inline' permet d'afficher les graphiques directement dans le notebook
%matplotlib inline

# Configuration du style visuel de seaborn pour des graphiques professionnels
sns.set_style("whitegrid")

# Configuration des dimensions par défaut des figures
plt.rcParams['figure.figsize'] = (12, 6)

# Configuration de la police pour une meilleure lisibilité
plt.rcParams['font.size'] = 10
```

**Explication post-code :**  
Ces bibliothèques forment l'écosystème standard de l'analyse de données en Python. Pandas gère les dataframes, NumPy les calculs, Matplotlib et Seaborn les visualisations.

---

### 3.2 Création et chargement des données

**Explication préalable :**  
En l'absence de fichier CSV externe, nous créons un dataset synthétique mais réaliste basé sur les données réelles de la Banque mondiale. Cette approche permet une démonstration complète de l'analyse.

```python
# Création d'un dictionnaire contenant les données du PIB
# Structure : années comme clés, données pays comme valeurs
donnees_pib = {
    'Annee': list(range(2015, 2024)),  # Liste des années de 2015 à 2023
    'Etats_Unis': [18238, 18745, 19543, 20612, 21433, 20893, 23315, 25462, 27360],
    'Chine': [11015, 11227, 12310, 13894, 14280, 14687, 17734, 17963, 17963],
    'Allemagne': [3377, 3479, 3693, 3951, 3861, 3846, 4259, 4082, 4456],
    'Japon': [4389, 4949, 4872, 4955, 5065, 5048, 4941, 4231, 4231],
    'Inde': [2104, 2296, 2652, 2713, 2870, 2671, 3177, 3386, 3737],
    'France': [2438, 2471, 2583, 2715, 2630, 2603, 2958, 2783, 3030]
}

# Conversion du dictionnaire en DataFrame pandas
# DataFrame = structure tabulaire bidimensionnelle avec étiquettes
df_pib = pd.DataFrame(donnees_pib)

# Affichage des 5 premières lignes pour vérification
print("Aperçu des données PIB (en milliards USD):")
print(df_pib.head())

# Création des données de population (en millions d'habitants)
donnees_population = {
    'Annee': list(range(2015, 2024)),
    'Etats_Unis': [321, 323, 325, 327, 329, 331, 332, 333, 334],
    'Chine': [1376, 1383, 1390, 1395, 1400, 1404, 1408, 1412, 1412],
    'Allemagne': [81.7, 82.5, 82.8, 83.0, 83.2, 83.2, 83.4, 83.3, 83.2],
    'Japon': [127, 127, 126.7, 126.5, 126.3, 125.8, 125.5, 125.1, 125],
    'Inde': [1311, 1339, 1366, 1393, 1417, 1407, 1417, 1425, 1430],
    'France': [66.5, 66.9, 67.1, 67.0, 67.4, 67.3, 67.6, 67.5, 67.0]
}

# Conversion en DataFrame
df_population = pd.DataFrame(donnees_population)

print("\nAperçu des données de population (en millions):")
print(df_population.head())
```

**Explication post-code :**  
Nous avons créé deux DataFrames : un pour le PIB et un pour la population. Ces données sont essentielles pour calculer le PIB par habitant et analyser les performances économiques relatives.

---

### 3.3 Nettoyage et transformation des données

**Explication préalable :**  
La transformation des données implique la restructuration (pivotage), le calcul de nouvelles métriques (PIB par habitant, taux de croissance) et la gestion des valeurs manquantes.

```python
# ÉTAPE 1: Restructuration des données PIB en format long
# Le format long facilite les analyses groupées et les visualisations
df_pib_long = df_pib.melt(
    id_vars=['Annee'],           # Colonne à conserver telle quelle
    var_name='Pays',              # Nom de la nouvelle colonne pour les pays
    value_name='PIB_Milliards'    # Nom de la colonne pour les valeurs
)

# ÉTAPE 2: Restructuration des données de population
df_pop_long = df_population.melt(
    id_vars=['Annee'],
    var_name='Pays',
    value_name='Population_Millions'
)

# ÉTAPE 3: Fusion des deux DataFrames
# Jointure sur 'Annee' et 'Pays' pour combiner PIB et population
df_complet = pd.merge(
    df_pib_long, 
    df_pop_long, 
    on=['Annee', 'Pays'],         # Clés de jointure
    how='inner'                    # Jointure interne (garde les correspondances)
)

# ÉTAPE 4: Calcul du PIB par habitant
# Formule: (PIB en milliards × 1000) / Population en millions = PIB en USD/habitant
df_complet['PIB_Par_Habitant'] = (
    df_complet['PIB_Milliards'] * 1000 / df_complet['Population_Millions']
)

# ÉTAPE 5: Calcul du taux de croissance annuel du PIB
# Formule: ((PIB_année_n - PIB_année_n-1) / PIB_année_n-1) × 100
# Tri préalable pour assurer l'ordre chronologique
df_complet = df_complet.sort_values(['Pays', 'Annee'])

# Calcul du taux de croissance avec décalage (shift) pour comparer à l'année précédente
df_complet['Taux_Croissance'] = df_complet.groupby('Pays')['PIB_Milliards'].pct_change() * 100

# ÉTAPE 6: Vérification de la qualité des données
# Comptage des valeurs manquantes par colonne
print("\nValeurs manquantes par colonne:")
print(df_complet.isnull().sum())

# ÉTAPE 7: Affichage du DataFrame final transformé
print("\nAperçu du DataFrame complet après transformation:")
print(df_complet.head(10))

# Statistiques de base pour validation
print("\nStatistiques descriptives:")
print(df_complet.describe())
```

**Explication post-code :**  
Nous avons transformé les données de format large à long, fusionné les datasets, calculé le PIB par habitant et les taux de croissance. Le taux de croissance de la première année de chaque pays sera NaN (normal car pas d'année précédente pour comparaison).

---

### 3.4 Préparation pour l'analyse

**Explication préalable :**  
Nous créons des vues spécifiques des données pour faciliter certaines analyses, notamment les données de l'année la plus récente et les moyennes par pays.

```python
# Extraction des données de l'année la plus récente (2023)
# Utile pour les comparaisons instantanées entre pays
annee_recente = df_complet['Annee'].max()  # Trouve l'année maximale
df_2023 = df_complet[df_complet['Annee'] == annee_recente].copy()

print(f"\nDonnées pour l'année {annee_recente}:")
print(df_2023)

# Calcul des moyennes par pays sur toute la période
# groupby() regroupe par pays, mean() calcule les moyennes
df_moyennes = df_complet.groupby('Pays').agg({
    'PIB_Milliards': 'mean',           # Moyenne du PIB
    'PIB_Par_Habitant': 'mean',        # Moyenne du PIB par habitant
    'Taux_Croissance': 'mean',         # Moyenne du taux de croissance
    'Population_Millions': 'mean'      # Moyenne de la population
}).round(2)  # Arrondi à 2 décimales

# Tri par PIB décroissant
df_moyennes = df_moyennes.sort_values('PIB_Milliards', ascending=False)

print("\nMoyennes par pays (2015-2023):")
print(df_moyennes)

# Création d'une fonction utilitaire pour formater les montants
def formater_milliards(x, pos):
    """
    Formate les nombres en milliards avec le symbole $
    Paramètres:
        x: valeur numérique
        pos: position (requis par FuncFormatter)
    Retourne: chaîne formatée
    """
    return f'${x:,.0f}B'

# Création du formateur pour réutilisation dans les graphiques
formateur_milliards = FuncFormatter(formater_milliards)
```

**Explication post-code :**  
Ces structures de données préparées (df_2023, df_moyennes) seront utilisées dans les analyses et visualisations. La fonction de formatage améliore la lisibilité des graphiques.

---

## 4. Analyse Statistique et Comparative

### 4.1 Statistiques descriptives générales

**Analyse préalable :**  
Les statistiques descriptives fournissent une vue d'ensemble de la distribution des données, identifiant les tendances centrales et la dispersion.

```python
# Calcul des statistiques descriptives par pays
print("=" * 80)
print("STATISTIQUES DESCRIPTIVES PAR PAYS")
print("=" * 80)

for pays in df_complet['Pays'].unique():
    # Filtrage des données pour le pays en cours
    df_pays = df_complet[df_complet['Pays'] == pays]
    
    print(f"\n{pays.upper()}")
    print("-" * 40)
    
    # PIB: Statistiques
    print(f"PIB (Milliards USD):")
    print(f"  - Moyenne: ${df_pays['PIB_Milliards'].mean():,.0f}B")
    print(f"  - Médiane: ${df_pays['PIB_Milliards'].median():,.0f}B")
    print(f"  - Écart-type: ${df_pays['PIB_Milliards'].std():,.0f}B")
    print(f"  - Min: ${df_pays['PIB_Milliards'].min():,.0f}B")
    print(f"  - Max: ${df_pays['PIB_Milliards'].max():,.0f}B")
    
    # PIB par habitant: Statistiques
    print(f"\nPIB par habitant (USD):")
    print(f"  - Moyenne: ${df_pays['PIB_Par_Habitant'].mean():,.0f}")
    print(f"  - Médiane: ${df_pays['PIB_Par_Habitant'].median():,.0f}")
    print(f"  - Écart-type: ${df_pays['PIB_Par_Habitant'].std():,.0f}")
    
    # Taux de croissance: Statistiques (on ignore les NaN)
    taux_valides = df_pays['Taux_Croissance'].dropna()
    print(f"\nTaux de croissance (%):")
    print(f"  - Moyenne: {taux_valides.mean():.2f}%")
    print(f"  - Médiane: {taux_valides.median():.2f}%")
    print(f"  - Écart-type: {taux_valides.std():.2f}%")
    print(f"  - Min: {taux_valides.min():.2f}%")
    print(f"  - Max: {taux_valides.max():.2f}%")
```

**Interprétation :**  
- **Moyenne vs Médiane** : Si la moyenne diffère significativement de la médiane, cela indique une asymétrie dans la distribution
- **Écart-type** : Mesure la volatilité économique du pays sur la période
- **Min/Max** : Identifie les années de récession ou de forte croissance

---

### 4.2 Comparaison entre pays (2023)

**Analyse préalable :**  
Nous comparons les performances relatives des pays sur l'année la plus récente disponible.

```python
# Création d'un tableau comparatif pour 2023
print("\n" + "=" * 80)
print("COMPARAISON INTERNATIONALE - ANNÉE 2023")
print("=" * 80)

# Tri par PIB décroissant
df_2023_trie = df_2023.sort_values('PIB_Milliards', ascending=False)

# Affichage du classement
print("\nClassement par PIB total:")
print("-" * 80)
for idx, (_, row) in enumerate(df_2023_trie.iterrows(), 1):
    print(f"{idx}. {row['Pays']:15} - ${row['PIB_Milliards']:>8,.0f}B")

# Classement par PIB par habitant
print("\n\nClassement par PIB par habitant:")
print("-" * 80)
df_2023_pib_hab = df_2023.sort_values('PIB_Par_Habitant', ascending=False)
for idx, (_, row) in enumerate(df_2023_pib_hab.iterrows(), 1):
    print(f"{idx}. {row['Pays']:15} - ${row['PIB_Par_Habitant']:>8,.0f}")

# Classement par taux de croissance
print("\n\nClassement par taux de croissance:")
print("-" * 80)
df_2023_croissance = df_2023.sort_values('Taux_Croissance', ascending=False)
for idx, (_, row) in enumerate(df_2023_croissance.iterrows(), 1):
    print(f"{idx}. {row['Pays']:15} - {row['Taux_Croissance']:>6.2f}%")

# Calcul des ratios de comparaison
# Rapport PIB US / PIB autres pays
print("\n\nRapport de taille économique (par rapport aux États-Unis):")
print("-" * 80)
pib_usa = df_2023[df_2023['Pays'] == 'Etats_Unis']['PIB_Milliards'].values[0]
for _, row in df_2023.iterrows():
    if row['Pays'] != 'Etats_Unis':
        ratio = (row['PIB_Milliards'] / pib_usa) * 100
        print(f"{row['Pays']:15} représente {ratio:5.1f}% du PIB américain")
```

**Interprétation :**  
- **Classement PIB total** : Reflète la puissance économique brute
- **Classement PIB/habitant** : Indicateur du niveau de vie et de développement
- **Classement croissance** : Indique le dynamisme économique récent
- **Ratios** : Permettent de contextualiser les écarts de taille

---

### 4.3 Évolution temporelle et tendances

**Analyse préalable :**  
Nous analysons comment le PIB a évolué dans le temps pour identifier les tendances de croissance et les périodes de choc.

```python
# Calcul de la croissance cumulée depuis 2015
print("\n" + "=" * 80)
print("ÉVOLUTION TEMPORELLE (2015-2023)")
print("=" * 80)

for pays in df_complet['Pays'].unique():
    df_pays = df_complet[df_complet['Pays'] == pays].sort_values('Annee')
    
    # PIB initial et final
    pib_initial = df_pays.iloc[0]['PIB_Milliards']
    pib_final = df_pays.iloc[-1]['PIB_Milliards']
    
    # Croissance cumulée en pourcentage
    croissance_cumulee = ((pib_final - pib_initial) / pib_initial) * 100
    
    # Taux de croissance annuel moyen composé (TCAM)
    # Formule: ((PIB_final/PIB_initial)^(1/n_années)) - 1
    nb_annees = len(df_pays) - 1
    tcam = (((pib_final / pib_initial) ** (1 / nb_annees)) - 1) * 100
    
    print(f"\n{pays}:")
    print(f"  PIB 2015: ${pib_initial:,.0f}B → PIB 2023: ${pib_final:,.0f}B")
    print(f"  Croissance cumulée: {croissance_cumulee:+.1f}%")
    print(f"  TCAM (Taux de croissance annuel moyen): {tcam:.2f}%")
    
    # Identification de la meilleure et pire année
    taux_valides = df_pays[df_pays['Taux_Croissance'].notna()]
    if len(taux_valides) > 0:
        meilleure_annee = taux_valides.loc[taux_valides['Taux_Croissance'].idxmax()]
        pire_annee = taux_valides.loc[taux_valides['Taux_Croissance'].idxmin()]
        
        print(f"  Meilleure année: {int(meilleure_annee['Annee'])} ({meilleure_annee['Taux_Croissance']:+.2f}%)")
        print(f"  Pire année: {int(pire_annee['Annee'])} ({pire_annee['Taux_Croissance']:+.2f}%)")
```

**Interprétation :**  
- **Croissance cumulée** : Mesure la performance totale sur la période
- **TCAM** : Standardise la comparaison en annualisant la croissance
- **Années extrêmes** : Identifie les chocs économiques (crises, rebonds)

---

### 4.4 Analyse de corrélation

**Analyse préalable :**  
Nous examinons les relations entre les différentes variables économiques pour identifier des patterns.

```python
# Calcul de la matrice de corrélation
# Sélection des variables numériques pertinentes
variables_numeriques = ['PIB_Milliards', 'PIB_Par_Habitant', 
                        'Taux_Croissance', 'Population_Millions']

# Calcul de la matrice de corrélation de Pearson
matrice_correlation = df_complet[variables_numeriques].corr()

print("\n" + "=" * 80)
print("MATRICE DE CORRÉLATION")
print("=" * 80)
print("\nCoefficients de corrélation de Pearson:")
print(matrice_correlation.round(3))

# Interprétation des corrélations significatives
print("\n\nInterprétation des corrélations notables:")
print("-" * 80)

# Seuil de corrélation significative
seuil = 0.5

for i in range(len(variables_numeriques)):
    for j in range(i+1, len(variables_numeriques)):
        var1 = variables_numeriques[i]
        var2 = variables_numeriques[j]
        corr = matrice_correlation.loc[var1, var2]
        
        if abs(corr) > seuil:
            force = "forte" if abs(corr) > 0.7 else "modérée"
            sens = "positive" if corr > 0 else "négative"
            print(f"{var1} ↔ {var2}:")
            print(f"  Corrélation {force} {sens} (r = {corr:.3f})")
```

**Interprétation :**  
- **r proche de 1** : Corrélation positive forte (variables évoluent ensemble)
- **r proche de -1** : Corrélation négative forte (variables évoluent inversement)
- **r proche de 0** : Pas de corrélation linéaire
- **PIB vs Population** : Souvent corrélés (pays plus peuplés ont des PIB plus élevés)
- **PIB/hab vs Croissance** : Peut révéler des patterns de développement

---

## 5. Visualisations Graphiques

### 5.1 Graphique en ligne : Évolution du PIB au fil du temps

**Explication préalable :**  
Ce graphique linéaire montre l'évolution du PIB de chaque pays de 2015 à 2023, permettant d'identifier les trajectoires de croissance et les points d'inflexion.

```python
# Création de la figure
plt.figure(figsize=(14, 7))

# Palette de couleurs professionnelle
couleurs = sns.color_palette("husl", n_colors=len(df_complet['Pays'].unique()))

# Tracé d'une ligne pour chaque pays
for idx, pays in enumerate(df_complet['Pays'].unique()):
    # Filtrage des données du pays
    df_pays = df_complet[df_complet['Pays'] == pays].sort_values('Annee')
    
    # Tracé de la ligne avec marqueurs
    plt.plot(df_pays['Annee'], 
             df_pays['PIB_Milliards'],
             marker='o',                    # Marqueurs circulaires
             linewidth=2.5,                 # Épaisseur de ligne
             markersize=6,                  # Taille des marqueurs
             label=pays,                    # Légende
             color=couleurs[idx],           # Couleur
             alpha=0.8)                     # Transparence

# Mise en forme du graphique
plt.title('Évolution du PIB (2015-2023)\nComparaison internationale', 
          fontsize=16, fontweight='bold', pad=20)
plt.xlabel('Année', fontsize=12, fontweight='bold')
plt.ylabel('PIB (Milliards USD)', fontsize=12, fontweight='bold')

# Configuration des axes
plt.xticks(range(2015, 2024), rotation=0)
plt.grid(True, alpha=0.3, linestyle='--')

# Légende positionnée de manière optimale
plt.legend(loc='upper left', frameon=True, shadow=True, fontsize=10)

# Ajout d'annotations pour les événements marquants
plt.axvline(x=2020, color='red', linestyle='--', alpha=0.5, linewidth=1)
plt.text(2020, plt.ylim()[1]*0.95, 'COVID-19', 
         ha='center', fontsize=9, color='red', fontweight='bold')

# Ajustement automatique de la mise en page
plt.tight_layout()

# Affichage du graphique
plt.show()
```

**Interprétation du graphique :**
- Les États-Unis maintiennent la plus grande économie avec une trajectoire ascendante constante
- La Chine montre une croissance rapide, réduisant l'écart avec les États-Unis
- Impact visible de la pandémie COVID-19 en 2020 (rupture de trajectoire)
- L'Inde affiche une croissance soutenue depuis 2020

---

### 5.2 Graphique en barres : Comparaison du PIB entre pays (2023)

**Explication préalable :**  
Un graphique en barres horizontales permet de comparer instantanément les tailles économiques relatives des pays en 2023.

```python
# Préparation des données pour 2023
df_2023_graph = df_2023.sort_values('PIB_Milliards', ascending=True)

# Création de la figure
plt.figure(figsize=(12, 7))

# Création du graphique en barres horizontales
barres = plt.barh(df_2023_graph['Pays'], 
                   df_2023_graph['PIB_Milliards'],
                   color=sns.color_palette("coolwarm", len(df_2023_graph)),
                   edgecolor='black',
                   linewidth=1.2)

# Ajout des valeurs sur les barres
for idx, (pays, valeur) in enumerate(zip(df_2023_graph['Pays'], 
                                           df_2023_graph['PIB_Milliards'])):
    plt
