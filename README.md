# Locuteur-Identification

# 🔊 Projet : Identification et Vérification du Locuteur

Ce projet implémente un système d'identification et de vérification du locuteur basé sur des enregistrements audio, utilisant des **Modèles de Mélange Gaussien (GMM)** et des **coefficients MFCC**. Deux méthodes de prétraitement vocal sont comparées : **WebRTC VAD** et **Librosa Split**. 
---

## 🎯 Objectifs

- Mettre en œuvre un système d'identification et de vérification basé sur la voix.
- Comparer deux techniques de suppression du silence (WebRTC VAD vs. Librosa).
- Évaluer l'impact du **nombre de gaussiennes** et de la **durée des segments audio**.
- Visualiser les performances via des **courbes DET** et mesurer le **Equal Error Rate (EER)**.

---

## 📦 Dataset

- **23 locuteurs** : 13 femmes (F1–F13), 10 hommes (H1–H10)
- **Entraînement** : 1 fichier de 2 minutes par locuteur
- **Test** : 15 fichiers par locuteur (5 × 5s, 5 × 10s, 5 × 15s)

---

## 🧰 Outils et bibliothèques utilisés

- `Python 3.x`
- `librosa` – traitement du signal audio
- `numpy`, `pandas` – traitement de données
- `soundfile` – sauvegarde audio
- `matplotlib` – visualisation
- `scikit-learn` – GMM et évaluation
- `webrtcvad` – détection d’activité vocale (VAD)
- `joblib` – sauvegarde des modèles

---

## 🔁 Pipeline de traitement

```text
1. Chargement des fichiers audio (16 kHz)
2. Suppression des silences :
   a. WebRTC VAD (trames 30 ms, PCM 16 bits)
   b. Librosa Split (top_db = 30)
3. Extraction MFCCs
4. Entraînement GMM (8 à 256 gaussiennes)
5. Identification & Vérification
6. Évaluation (courbes DET, EER)
