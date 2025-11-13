Air Quality Dataset

DOI : 10.24432/C59K5F
Source : UCI Machine Learning Repository (UCI) 
DOI

Description

La base de données contient les réponses horaires moyennes d’un dispositif multisenseur de gaz déployé sur le terrain dans une ville italienne. 
DOI

Elle inclut également des valeurs de concentrations de gaz mesurées par un analyseur certifié co-localisé. 
DOI

Caractéristiques principales

Type de données : Multivariée, série temporelle. 
DOI

Sujet : Informatique (Computer Science) — tâche de régression. 
DOI

Nombre d’instances : 9 358 (heures) 
DOI

Nombre de caractéristiques : 15 
DOI

Présence de valeurs manquantes : Oui — les valeurs manquantes sont codées par « -200 ». 
DOI

Variables / Attributs

Voici un résumé des variables : 
DOI

Variable	Type	Description
Date	Feature	Date (JJ/MM/AAAA)
Time	Feature	Heure (HH.MM.SS)
CO(GT)	Feature	Concentration horaire moyenne de CO (mg/m³) – analyseur de référence
PT08.S1(CO)	Feature	Réponse horaire moyenne du capteur (ciblé CO)
NMHC(GT)	Feature	Concentration horaire moyenne d’hydrocarbures non-méthaniques (µg/m³)
C6H6(GT)	Feature	Concentration horaire moyenne de benzène (µg/m³)
PT08.S2(NMHC)	Feature	Réponse horaire moyenne du capteur (ciblé NMHC)
NOx(GT)	Feature	Concentration horaire moyenne de NOx (ppb)
PT08.S3(NOx)	Feature	Réponse horaire moyenne du capteur (ciblé NOx)
NO2(GT)	Feature	Concentration horaire moyenne de NO₂ (µg/m³)
PT08.S4(NO2)	Feature	Réponse horaire moyenne du capteur (ciblé NO₂)
PT08.S5(O3)	Feature	Réponse horaire moyenne du capteur (ciblé O₃)
T	Feature	Température (°C)
RH	Feature	Humidité relative (%)
AH	Feature	Humidité absolue
Population / Zone géographique / Période

Zone géographique : Une ville italienne, dans une zone fortement polluée, au niveau de la route. 
DOI

Période : de mars 2004 à février 2005 (une année complète) 
DOI

Population : Ce ne sont pas des données individuelles (personnes), mais des mesures horaires d’un dispositif de capteurs et d’un analyseur de référence dans l’environnement urbain.

Licence et utilisation

Licence : Creative Commons Attribution 4.0 International (CC BY 4.0) 
DOI

Usage : Utilisable pour la recherche. Usage commercial exclu (à vérifier selon les termes exacts). 
DOI

Usage / Application

Typiquement utilisée pour des tâches de régression, calibration de capteurs, détection de dérive des capteurs, analyse des séries temporelles de pollution de l’air. 
DOI

Peut servir à la recherche en qualité de l’air, capteurs environnementaux, modélisation de la pollution urbaine, apprentissage automatique appliqué aux signaux environnementaux.

Notes / Limitations

Il existe des valeurs manquantes codées « -200 ». 
DOI

Le capteur multisenseur montre des effets de dérive (“sensor drift”) et des sensibilités croisées (“cross-sensitivities”), ce qui peut affecter l’estimation des concentrations. 
DOI

Le contexte est spécifique à une seule ville italienne (donc attention à la généralisation).

Il s’agit de mesures horaires, donc résolution temporelle relativement fine, mais aucune donnée géographique très granulée (par exemple localisation fine de capteur) n’est explicitée.
