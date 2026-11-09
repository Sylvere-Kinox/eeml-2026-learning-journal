# Jour 2 — Apprentissage par Renforcement & Estimateurs Statistiques Appris

> **Date** : 28 juillet 2026  
> **Intervenants principaux** : Kyunghyun Cho (NYU), Miruna Pislar (DeepMind)  
> **Thèmes** : Fondements du RL, PPO, GRPO & DeepSeek-R1, « Statistics Upside Down » (Set Transformer++, MIST).  
> **Documents disponibles** :
> - 📄 **[Lire les notes complètes en PDF](eeml-2026-day2-rl.pdf)** *(13 pages, lisible directement sur GitHub)*
> - 📝 **[Document source Word éditable](EEML_2026_Jour2_Notes.docx)**

---

## 🎯 Vue d'ensemble en un coup d'œil

### 1. Apprentissage par renforcement (RL) moderne
* **Le formalisme MDP (Markov Decision Process)** : État $s$, action $a$, transition $\mathcal{P}(s'|s,a)$, récompense $r(s,a)$ et facteur d'actualisation $\gamma$.
* **Bandits manchots & Compromis exploration/exploitation** : Algorithmes UCB (*Upper Confidence Bound*) et échantillonnage de Thompson.
* **Algorithmes Policy-Based vs Value-Based** :
  - Équations de Bellman pour $V(s)$ et $Q(s,a)$.
  - Différence temporelle (TD-Learning) vs Monte Carlo.
  - Du Q-learning classique au Deep Q-Network (DQN) avec *replay buffer* et réseau cible (*target network*).
* **Actor-Critic & Méthodes de pointe pour les LLM** :
  - **PPO (Proximal Policy Optimization)** : Écrêtage (*clipping*) du ratio de probabilité pour garantir des mises à jour stables sans dégradation brutale de politique.
  - **RLHF & GRPO (Group Relative Policy Optimization)** : Analyse de la méthode employée par les modèles de raisonnement récents (comme **DeepSeek-R1**) avec récompenses vérifiables basées sur des règles d'exactitude (tests de code, calcul formel) éliminant le besoin d'un modèle critique lourd.

### 2. Statistics Upside Down (Kyunghyun Cho)
* **Changer de paradigme sur l'estimation statistique** : Au lieu de dériver analytiquement des estimateurs statistiques sous des hypothèses rigides de distribution (gaussienne, i.i.d.), **apprendre l'estimateur lui-même** à l'aide d'un réseau de neurones.
* **Le biais caché de l'écart-type** : Démonstration que l'estimateur classique sans biais de la variance $\hat{\sigma}^2$ produit un estimateur biaisé de l'écart-type $\sigma$ par l'inégalité de Jensen ($\mathbb{E}[\sqrt{X}] \le \sqrt{\mathbb{E}[X]}$).
* **Architecture Set Transformer++** : Traiter un échantillon statistique comme un ensemble non ordonné (invariance par permutation) grâce à des mécanismes d'auto-attention sans encodage positionnel.
* **MIST (Mutual Information Neural Estimator)** : Estimer l'information mutuelle entre variables aléatoires en haute dimension avec calibration quantile.

### 3. Atelier pratique (Hands-on)
* Implémentation progressive de REINFORCE dans l'environnement *CliffWalking*, incorporation de la baseline pour réduire la variance du gradient, puis transition vers Actor-Critic.

---

## 💡 Idée clé : GRPO (Group Relative Policy Optimization)

Au lieu d'entraîner un modèle critique $V_\phi(s)$ séparé (qui consomme autant de mémoire GPU que le modèle de génération), **GRPO** échantillonne un groupe de $G$ réponses $\{y_1, y_2, \dots, y_G\}$ pour chaque invite $x$, évalue les récompenses $\{r_1, r_2, \dots, r_G\}$ et calcule l'avantage normalisé :

$$\hat{A}_i = \frac{r_i - \text{moyenne}(\{r_j\})}{\text{écart-type}(\{r_j\})}$$

Ce mécanisme permet d'aligner efficacement les modèles de raisonnement complexes avec une empreinte mémoire réduite.

---

📖 **Pour approfondir les dérivations d'algorithmes et les architectures :** consultez **[eeml-2026-day2-rl.pdf](eeml-2026-day2-rl.pdf)**.
