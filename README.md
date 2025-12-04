## 📁 Structure du projet

# projet-maintenance-predictive
Ce projet vise à prédire les pannes d’un équipement industriel en utilisant des données historiques et des modèles de machine learning. L’objectif est d’anticiper les défaillances avant qu’elles ne se produisent afin de réduire les coûts de maintenance, améliorer la fiabilité des machines et éviter les arrêts non planifiés.
# 🔧 Projet de Maintenance Prédictive

Ce projet vise à prédire les pannes d’un équipement industriel à partir de données historiques comprenant les caractéristiques opérationnelles de la machine (température, vitesse, couple, usure, etc.).  
L’objectif principal est d’anticiper les défaillances avant qu’elles n’entraînent des arrêts non planifiés, permettant ainsi :

- ✔️ d’améliorer la fiabilité du système  
- ✔️ de réduire les coûts de maintenance  
- ✔️ d’optimiser la production  
- ✔️ d’intervenir avant la panne réelle  

---

# 📁 Structure du projet


---

# 📊 Jeu de données

Le dataset utilisé provient de mesures industrielles simulées.  
Il comprend les variables suivantes :

- **Air Temperature**
- **Process Temperature**
- **Rotational Speed (rpm)**
- **Torque (Nm)**
- **Tool Wear (min)**
- **Type de produit (L, M, H)**
- **Failure Type (cible)**  
  - No Failure  
  - Heat Dissipation Failure  
  - Power Failure  
  - Overstrain Failure  
  - Tool Wear Failure  
  - Random Failure  

Format :  
📄 `predictive_maintenance_clean2.xlsx`

---

# 🧪 Analyse Exploratoire (EDA)

Une exploration des données a été réalisée pour étudier :

- les distributions des variables  
- les corrélations  
- les anomalies  
- les signaux avant-panne  

Voici quelques visualisations extraites du PDF du projet :

## 🔥 Histogramme d'une variable
![Histogramme](images/page5_img1.png)

## 📈 Distribution d’une autre mesure
![Distribution](images/page6_img1.png)

## 🧩 Matrice de corrélation
![Correlation Matrix](images/page14_img1.png)

## 🔧 Analyse des types de pannes
![Failure Types](images/page21_img1.png)

*(Les images présentes ci-dessus sont automatiquement extraites du PDF fourni.)*

---

# 🤖 Modèles de Machine Learning utilisés

Plusieurs modèles équilibrés ont été testés pour optimiser la prédiction des pannes :

- **Balanced Random Forest Classifier**
- **Balanced Bagging Classifier**
- **RUSBoost Classifier**
- **Easy Ensemble Classifier**
- **Voting Classifier**

📌 Le meilleur modèle a été sélectionné selon :
- Accuracy  
- F1-score  
- Courbes de précision-rappel  
- Score de classification équilibré  

---

# ⚠️ Exemple d’Avertissement de Panne

Voici un exemple de message généré par le modèle :


---

# 🧠 Notebook du projet

Toute l’analyse détaillée, le nettoyage des données et la construction des modèles se trouvent dans :

👉 `notebooks/exploration.ipynb`

Il contient :
- Analyse exploratoire  
- Visualisations  
- Préparation des données  
- Entraînement des modèles  
- Comparaison des performances  
- Sélection du meilleur modèle  

---
