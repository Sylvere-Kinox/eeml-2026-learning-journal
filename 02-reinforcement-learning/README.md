# Jour 2 — Apprentissage par renforcement et estimateurs statistiques appris

Date : 28 juillet 2026  
Intervenants : Kyunghyun Cho (NYU), Miruna Pislar (DeepMind)  
Thèmes : Fondements du RL, PPO, GRPO, Statistics Upside Down (Set Transformer++, MIST).

Documents :
- [Notes complètes (PDF)](eeml-2026-day2-rl.pdf)
- [Document source Word](EEML_2026_Jour2_Notes.docx)

## Synthèse

### 1. Apprentissage par renforcement
- **Formalisme MDP** : état $s$, action $a$, transitions $\mathcal{P}(s'|s,a)$, récompense $r(s,a)$ et facteur d'actualisation $\gamma$.
- **Bandits multi-bras** : compromis exploration/exploitation, bornes de confiance (UCB) et échantillonnage de Thompson.
- **Méthodes par valeur et par politique** :
  - Équations de Bellman pour $V(s)$ et $Q(s,a)$.
  - Différence temporelle (TD) vs Monte Carlo.
  - Deep Q-Networks (DQN) avec mémoire de rejeu et réseau cible.
- **Actor-Critic et alignement de modèles** :
  - Proximal Policy Optimization (PPO) : stabilisation des mises à jour par écrêtage du ratio de vraisemblance.
  - Group Relative Policy Optimization (GRPO) : calcul de l'avantage à partir d'un groupe d'échantillons avec récompenses vérifiables (utilisé dans DeepSeek-R1), évitant l'entraînement d'un modèle critique dédié.

### 2. Statistics Upside Down
- **Apprentissage d'estimateurs statistiques** : apprentissage direct d'estimateurs paramétrés par des réseaux de neurones plutôt que dérivation analytique sous hypothèses de distribution classiques.
- **Biais de l'écart-type** : biais introduit par l'inégalité de Jensen lors du passage de l'estimateur non biaisé de la variance à l'écart-type.
- **Set Transformer++** : modèle traitant des ensembles non ordonnés (invariance par permutation) via l'auto-attention.
- **MIST** : estimation de l'information mutuelle en grande dimension.

## Formule clé : Avantage normalisé dans GRPO

Pour un groupe de $G$ sorties $\{y_1, \dots, y_G\}$ générées pour une même invite avec récompenses $\{r_1, \dots, r_G\}$ :

$$\hat{A}_i = \frac{r_i - \text{moyenne}(\{r_j\})}{\text{écart-type}(\{r_j\})}$$
