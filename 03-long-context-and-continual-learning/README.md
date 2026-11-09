# Jour 3 — Contexte Long dans les LLMs, Capital-Risque & Apprentissage Continu

> **Date** : 29 juillet 2026  
> **Intervenants principaux** : Federico Barbara, Máté Mitk, Claire Lyle & Razvan Pascanu  
> **Thèmes** : Encodages RoPE, Attention Sinks, Écosystème Startup & VC, Oubli Catastrophique (Continual Learning).  
> **Documents disponibles** :
> - 📄 **[Lire les notes complètes en PDF](eeml-2026-day3-llm-continual.pdf)** *(13 pages, lisible directement sur GitHub)*
> - 📝 **[Document source Word éditable](EEML_2026_Jour3_Notes.docx)**

---

## 🎯 Vue d'ensemble en un coup d'œil

### 1. Contexte long dans les modèles de langage (LLMs)
* **Le défi « Entraîner court, généraliser long »** : Pourquoi un LLM entraîné sur 4k tokens échoue naturellement lorsqu'on lui en soumet 32k ou 128k en inférence (dérive distributionnelle des positions).
* **Défaillances mécaniques observées** :
  - Dégradation des capacités de comptage et de copie exacte.
  - Phénomène de l'« aiguille dans une botte de foin » (*Needle In A Haystack*) et effet *Lost in the Middle*.
* **Attention Sinks & Dispersion d'attention** : Découverte que les premiers tokens de la séquence agissent comme des puits d'absorption d'attention indispensables à la stabilité numérique du Softmax, même s'ils n'ont pas de valeur sémantique forte (StreamingLLM).
* **Rotary Position Embeddings (RoPE) & Adaptation (ex. Gemma)** :
  - Représentation complexe des vecteurs Query et Key par multiplication par une matrice de rotation orthogonale.
  - Techniques d'extension de contexte : interpolation linéaire des positions vs scaling basé sur la fréquence (NTK-aware RoPE, YaRN).

### 2. Capital-risque (VC) pour fondateurs techniques
* Comprendre le modèle mental des investisseurs en amorçage (*Seed/Series A*) dans l'écosystème IA européen et mondial.
* Notions clés : valorisation pré/post-money, dilution, clauses de protection (*liquidation preferences*, *vesting*), et passage d'un prototype de recherche à un produit avec avantage compétitif défendable (*moat*).

### 3. Apprentissage continu (*Continual Learning*)
* **L'Oubli Catastrophique (*Catastrophic Forgetting*)** : Pourquoi les réseaux de neurones écrasent brutalement les connaissances passées lorsqu'ils apprennent une nouvelle tâche séquentielle.
* **Les trois grandes familles de solutions** :
  1. **Méthodes par rejeu (*Replay-based*)** : Buffer de mémoire épisodique ou génération synthétique d'exemples passés.
  2. **Régularisation sur les paramètres (*Regularization-based*)** : Protection des poids critiques pour les tâches antérieures via la matrice d'information de Fisher (algorithme **EWC — Elastic Weight Consolidation**).
  3. **Isolation architecturale (*Parameter-isolation*)** : Allocation dynamique de sous-réseaux ou adaptateurs modulaires gelés (modules LoRA dédiés par tâche).

---

## 💡 Idée clé : La mécanique de RoPE (Rotary Position Embedding)

Pour encoder la position $m$, RoPE transforme une paire de dimensions $(q_1, q_2)$ du vecteur de requête comme une rotation dans le plan complexe :

$$R_{\Theta, m} \mathbf{x} = \begin{pmatrix} \cos(m\theta) & -\sin(m\theta) \\ \sin(m\theta) & \cos(m\theta) \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \end{pmatrix}$$

Cette propriété remarquable assure que le produit scalaire $\langle R_m \mathbf{q}, R_n \mathbf{k} \rangle$ ne dépend que de la distance relative $m - n$, tout en permettant une manipulation géométrique continue des positions lors de l'extension de contexte.

---

📖 **Pour approfondir les détails d'implémentation et les analyses comparatives :** consultez **[eeml-2026-day3-llm-continual.pdf](eeml-2026-day3-llm-continual.pdf)**.
