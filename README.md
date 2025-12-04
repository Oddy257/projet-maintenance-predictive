# 🛠️ Analyse et Anticipation des Défaillances Machines via Machine Learning

Projet réalisé dans le cadre du module **Intelligence Artificielle et ses Applications**  
Filière **Génie Industriel et Logistique – 2ᵉ année cycle d’ingénieur**. :contentReference[oaicite:0]{index=0}  

**Encadré par :** Pr. A. CHAREF  
**Réalisé par :**  
- Mouna Bahi  
- Odette Niyokwizera  
- Nouhaila Hamdach  
- Hiba Fettache  

---

## 🔍 1. Contexte et problématique

Dans l’industrie, les machines sont soumises à des contraintes mécaniques, thermiques et électriques qui peuvent provoquer des **pannes imprévues**. Ces défaillances entraînent : :contentReference[oaicite:1]{index=1}  

- des **arrêts non planifiés** de la production,  
- des **coûts élevés** de maintenance corrective,  
- un **manque de visibilité** sur l’état réel des équipements,  
- une prise de décision souvent **réactive** plutôt que proactive.  

🎯 **Problème central :**  
> Comment utiliser les données de capteurs pour **prédire l’apparition d’une panne** et **identifier son type** avant qu’elle ne se produise ?

---

## 🎯 2. Objectifs du projet

L’objectif de ce projet est de développer un système de **maintenance prédictive** capable de : :contentReference[oaicite:2]{index=2}  

- Prédire si **une machine va tomber en panne ou non** (*classification binaire*).  
- Identifier **le type de défaillance** (Tool Wear, Heat Dissipation, Overstrain, Power Failure, Random Failure…).  
- Mettre en évidence les **zones de fonctionnement à risque** (combinaisons vitesse / couple / température).  
- Fournir des **avertissements** permettant de planifier la maintenance avant la panne.

---

## 🗂️ 3. Présentation du dataset

Le dataset utilisé provient d’un cas de **maintenance prédictive industrielle** synthétique, contenant **10 000 observations** et **10 variables**. :contentReference[oaicite:3]{index=3}  

### 🔹 Variables explicatives (features)

- **Type** : qualité du produit (`L`, `M`, `H`)  
- **Air temperature [K]** : température de l’air  
- **Process temperature [K]** : température du processus  
- **Rotational speed [rpm]** : vitesse de rotation  
- **Torque [Nm]** : couple mécanique  
- **Tool wear [min]** : usure de l’outil  

### 🎯 Variables cibles (targets)

- **Target** : 0 = pas de panne, 1 = panne  
- **Failure Type** : type de panne (par ex. `Heat Dissipation Failure`, `Tool Wear Failure`, etc.)

---

## 🧼 4. Data Cleaning & EDA (Exploration des données)

Les étapes principales réalisées : :contentReference[oaicite:4]{index=4}  

1. **Chargement des données** (Excel → Pandas).  
2. **Vérification de la qualité des données** :  
   - doublons, valeurs manquantes, erreurs.  
3. **Analyse descriptive** : moyennes, écarts-types, distributions.  
4. **Visualisation des distributions** (histogrammes) et des corrélations.  

### 🔎 Corrélations importantes

- Le **couple (Torque)** et la **vitesse de rotation** sont fortement corrélés.  
- La **température du processus** suit l’évolution de la **température de l’air**.  

> On observe que les pannes surviennent pour des **valeurs extrêmes** de couple et de vitesse de rotation : il existe une zone de fonctionnement normale, et au-delà, le risque de panne augmente fortement. :contentReference[oaicite:5]{index=5}  

---

## 🧠 5. Méthodologie de modélisation

### 🧩 Préparation des données

- Encodage de la variable **Type** et des catégories de défaillances.  
- Normalisation / standardisation des variables continues.  
- Séparation **Train / Test** avec **stratification** pour conserver la proportion des classes minoritaires (pannes rares). :contentReference[oaicite:6]{index=6}  

### 🤖 Modèles testés

Plusieurs modèles de classification ont été testés :  

- **Random Forest Classifier**  
- **Balanced Random Forest**  
- **Balanced Bagging Classifier**  
- **RUSBoost**  
- **EasyEnsemble**  

Les modèles “balanced” permettent de mieux gérer le **déséquilibre de classes** (peu de pannes par rapport aux non-pannes).

Cette section présente les modèles de Machine Learning testés pour la prédiction des pannes, ainsi que leur comportement général sur les données.

![Modèles testés](images/exploration_1.png)

## 📈 6. Évaluation des modèles

L’évaluation est réalisée à l’aide de :  

- **Accuracy** (taux de bonne classification)  
- **Recall** (capacité à détecter les pannes)  
- **Precision**  
- **F1-score**  
- **Matrice de confusion**  

> Le train/test stratifié garantit que le **jeu de test** est représentatif du dataset complet, même pour les classes minoritaires. :contentReference[oaicite:7]{index=7}  

Le modèle final retenu est celui qui offre le meilleur compromis entre :  
✅ bonne performance globale  
✅ bonne détection des pannes (éviter les faux négatifs)  

Les performances des modèles ont été évaluées selon plusieurs métriques : précision, rappel, F1-score, matrice de confusion, etc.  
La visualisation ci-dessous résume ces résultats.

![Évaluation des modèles](images/exploration_2.png)

## 📌 7. Interprétation & zones de risque

L’analyse conjointe de la **vitesse de rotation**, du **couple** et des **types de pannes** montre des zones caractéristiques : :contentReference[oaicite:8]{index=8}  

- **Power Failure** : vitesses faibles + couples élevés  
- **Tool Wear Failure** : vitesses moyennes à élevées + couples modérés  
- **Overstrain Failure** : couples très élevés (≈ 47–68 Nm)  
- **Heat Dissipation Failure** : vitesses faibles / moyennes + couples élevés  

👉 Ces observations permettent d’identifier des **zones de fonctionnement critique** et de proposer des **seuils d’alerte**.

Cette section met en évidence les zones de fonctionnement où la machine est susceptible de tomber en panne :  
plages de couples, températures, vitesses de rotation ou usures d’outil considérées comme critiques.

![Interprétation et zones de risque](images/exploration_3.png)


## 🚨 8. Exemple d’avertissement généré

Lorsqu’une nouvelle observation dépasse certains seuils critiques, le système peut générer un message de maintenance prédictive :

```text
⚠️ AVERTISSEMENT DE MAINTENANCE PRÉDICTIVE

Machine : #A17
Date : 2025-01-05 14:32

Risque de panne détecté.

Paramètres mesurés :
- Vitesse de rotation : 1480 rpm
- Couple : 57 Nm
- Température du processus : 314 K
- Usure de l’outil : 8 min

Type de défaillance probable : Tool Wear Failure

Action recommandée :
▶ Planifier une inspection de l’outil
▶ Prévoir un remplacement avant le prochain cycle de production


