# Jour 3 — Contexte long dans les LLM, capital-risque et apprentissage continu

Date : 29 juillet 2026  
Intervenants : Federico Barbara, Máté Mitk, Claire Lyle, Razvan Pascanu  
Thèmes : Contexte long, Rotary Position Embeddings (RoPE), puits d'attention, investissement VC, oubli catastrophique.

Documents :
- [Notes complètes (PDF)](eeml-2026-day3-llm-continual.pdf)
- [Document source Word](EEML_2026_Jour3_Notes.docx)

## Synthèse

### 1. Contexte long dans les modèles de langage
- **Généralisation en longueur** : écart entre longueur d'entraînement et longueur d'inférence.
- **Défaillances observées** : dégradation sur les tâches de comptage, copie et récupération d'information ciblée (*Needle In A Haystack*).
- **Puits d'attention (Attention Sinks)** : rôle stabilisateur des premiers jetons dans l'attention Softmax (StreamingLLM).
- **Rotary Position Embeddings (RoPE)** : encodage de positions relatives par rotation dans le plan complexe et techniques d'extension (interpolation linéaire, NTK-aware scaling).

### 2. Notions de capital-risque
- Principes de financement pour projets technologiques : valorisation pré/post-money, dilution du capital, termes contractuels de protection et modèle économique.

### 3. Apprentissage continu (Continual Learning)
- **Oubli catastrophique** : écrasement des connaissances antérieures lors d'apprentissages séquentiels.
- **Approches principales** :
  - Méthodes par rejeu d'exemples antérieurs (mémoire épisodique ou données synthétiques).
  - Régularisation sur les paramètres (Elastic Weight Consolidation - EWC avec la matrice d'information de Fisher).
  - Isolation de paramètres et modules dynamiques (adaptateurs LoRA dédiés).

## Formule clé : Encodage RoPE

Pour deux composantes de dimension $(x_1, x_2)$ à la position $m$ :

$$R_{\Theta, m} \mathbf{x} = \begin{pmatrix} \cos(m\theta) & -\sin(m\theta) \\ \sin(m\theta) & \cos(m\theta) \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \end{pmatrix}$$
