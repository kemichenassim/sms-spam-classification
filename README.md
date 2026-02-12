# 📱 Classification de SMS Spam  
### Prétraitement Textuel & Apprentissage Profond  
**Évaluation Sommative UA3 – Intelligence Artificielle**

---

## 🎯 Objectif du projet

Ce projet vise à développer et comparer plusieurs approches de classification de SMS (Ham vs Spam) en utilisant :

- 📝 Prétraitement textuel avancé  
- 🔢 Vectorisation TF-IDF  
- 🔄 Autoencodeur (réduction non-supervisée)  
- 🤖 BERT (Transformers – embeddings contextuels)

L’objectif principal est d’identifier la meilleure approche dans un contexte de **dataset déséquilibré**.

---

## 📊 Dataset

- **Nom** : SMS Spam Collection  
- **Source** : UCI Machine Learning Repository  
- **Nombre total de messages** : 5 572  

### Distribution des classes

| Classe | Nombre | Pourcentage |
|--------|--------|------------|
| Ham (Légitime) | 4 825 | 86.6% |
| Spam | 747 | 13.4% |

⚠️ Le dataset est fortement déséquilibré.  
L’accuracy seule n’est donc pas une métrique fiable.

---

## 🔍 Analyse Exploratoire (EDA)

- Aucune valeur manquante  
- 5 169 messages uniques  
- Les messages SPAM sont en moyenne **deux fois plus longs** que les messages HAM  
- La longueur du message constitue une caractéristique discriminante importante  

---

## 🔧 Pipeline de Prétraitement

1. Conversion en minuscules  
2. Suppression de la ponctuation et caractères spéciaux  
3. Tokenisation  
4. Suppression des stopwords  
5. Lemmatisation  


## 📐 Approches Comparées

### 1️⃣ TF-IDF + Réseau Dense

- max_features = 5000  
- ngram_range = (1,2)  
- Réseau dense (128 → 64 → 32 → 1)  

**Résultats :**

- Accuracy : 97.58%  
- AUC-ROC : 0.9828  
- Recall Spam : 87%  

✅ Excellent compromis performance / simplicité  

---

### 2️⃣ Autoencodeur (Réduction non-supervisée)

Compression : 5000 → 64 dimensions  

**Résultats :**

- Accuracy : 86.64%  
- AUC-ROC : 0.4127  
- Recall Spam : 0%  

❌ Échec critique  

Le modèle prédit tout comme "Ham".  
L’accuracy est trompeuse dans un dataset déséquilibré.

📌 Leçon fondamentale :  
L’accuracy seule peut être dangereusement trompeuse.

---

### 3️⃣ BERT (Transformers)

- Modèle : bert-base-uncased  
- 110 millions de paramètres  
- Embeddings de 768 dimensions  

**Résultats :**

- Accuracy : 98.25%  
- AUC-ROC : 0.9974  
- Recall Spam : 91%  

🏆 Meilleure performance globale  

---

## 🏆 Classement Final

| Rang | Modèle | Accuracy | AUC |
|------|--------|----------|-----|
| 🥇 | BERT | 98.25% | 0.9974 |
| 🥈 | TF-IDF | 97.58% | 0.9828 |
| 🥉 | Autoencodeur | 86.64% | 0.4127 |

---

## 📈 Enseignements Clés

- L’accuracy est insuffisante pour les datasets déséquilibrés  
- Toujours analyser Recall et AUC-ROC  
- La réduction non-supervisée peut perdre l’information discriminante  
- BERT capture la sémantique contextuelle et améliore significativement la performance  

---

## 🚀 Améliorations Futures

### Court terme
- Fine-tuning de BERT  
- Pondération des classes (class_weight)  
- Équilibrage via SMOTE  

### Long terme
- Ensemble de modèles  
- Autoencodeur supervisé  
- Optimisation des hyperparamètres (GridSearch)  
- Déploiement en production  

---

## 💡 Stratégie Hybride Proposée

Utiliser :

- TF-IDF pour filtrage rapide (majorité des cas)  
- BERT pour les cas ambigus  

Optimisation du ratio coût / performance.

---

## 🛠️ Technologies Utilisées

- Python  
- Scikit-learn  
- TensorFlow / Keras  
- HuggingFace Transformers  
- NLTK / SpaCy  
- Matplotlib / Seaborn  

---

## 👨‍🎓 Auteur

**Kemiche Nassim**  
Étudiant en Science des Données  
Collège La Cité  

GitHub : https://github.com/kemichenassim

