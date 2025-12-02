# 🛠️ Projet de Maintenance Prédictive

Ce projet utilise le machine learning pour prédire les pannes d’une machine industrielle en analysant plusieurs paramètres :

- Température de l’air  
- Température du processus  
- Vitesse de rotation  
- Couple (Torque)  
- Usure de l’outil  
- Type de la pièce

L’objectif est d’anticiper les pannes pour réduire :
✔️ les arrêts de production  
✔️ les coûts de maintenance  
✔️ les risques d’endommagement des machines  

## 🔍 Fonctionnement
1. Les données de la machine sont collectées.  
2. Le modèle analyse l’évolution des paramètres.  
3. Si un comportement anormal apparaît ➜ **un avertissement est généré**.  
4. Le modèle prédit le type de panne probable.

## 📊 Modèle utilisé
- Balanced Random Forest  
- Balanced Bagging Classifier  
- RUSBoost  
- Easy Ensemble  

Le modèle final est enregistré dans :  
**`pipeline_best_model.pkl`**

## 🔔 Exemple d’avertissement généré
