# 💻 Laptop Price Prediction - Deep Learning 

Ce projet a été réalisé dans le cadre du cours de **Deep Learning** du Master **MDS** à l'**Université Mundiapolis**. L'objectif est de prédire le prix des ordinateurs portables en utilisant une approche de régression par réseaux de neurones.

## 📝 Présentation du Projet
L'enjeu est de transformer un dataset brut contenant des spécifications techniques textuelles en données numériques exploitables pour entraîner un modèle **PyTorch** capable d'estimer la valeur marchande d'un laptop.

## 📊 Jeu de Données
Le fichier `laptop_price.csv` comprend 1303 entrées avec les colonnes suivantes :
- **Marque et Modèle** : Company, Product, TypeName.
- **Écran** : Inches, ScreenResolution.
- **Matériel** : Cpu, Ram, Gpu.
- **Stockage et Poids** : Memory, Weight.
- **Cible** : Price_euros.

## 🛠️ Ingénierie des Données (Feature Engineering)
C'est l'étape cruciale du projet. Le notebook effectue les transformations suivantes :
- **Extraction CPU** : Séparation de la marque, du type et de la fréquence (ex: 2.5GHz).
- **Nettoyage RAM & Poids** : Suppression des unités ('GB', 'kg') et conversion en types numériques.
- **Analyse du Stockage** : Utilisation d'expressions régulières (**Regex**) pour extraire la capacité totale en Go et le type de disque (SSD, HDD, Flash).
- **Résolution d'écran** : Conversion de la résolution en nombre total de pixels.
- **Encodage** : Application du One-Hot Encoding, augmentant le nombre de variables à **864**.



## 🧠 Architecture du Modèle
Le modèle est un réseau de neurones de type **Perceptron Multicouche (MLP)** conçu avec **PyTorch** :
- **Couche d'entrée** : 864 neurones.
- **Couche cachée 1** : 32 neurones, activation ReLU.
- **Couche cachée 2** : 16 neurones, activation ReLU.
- **Couche de sortie** : 1 neurone (valeur continue du prix).



### Configuration de l'entraînement
- **Optimiseur** : Adam (Learning rate = 0.001).
- **Fonction de perte** : Mean Squared Error (MSE).
- **Époques** : 300.
- **Batch size** : 32 (Train) / 64 (Test).

## 📈 Résultats et Évaluation
Les performances du modèle sont évaluées sur un ensemble de test (20% des données) :

| Métrique | Valeur approximative |
| :--- | :--- |
| **MSE** | ~200,732 |
| **RMSE** | ~448.03 € |
| **MAE** | ~308.70 € |

La courbe d'apprentissage montre une convergence stable de la perte MSE au fil des époques.

## 🚀 Installation et Utilisation
1. Cloner ce dépôt ou télécharger le notebook.
2. Installer les dépendances :
   ```bash
   pip install torch pandas numpy matplotlib seaborn scikit-learn
