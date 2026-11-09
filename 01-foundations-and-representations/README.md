# Jour 1 — Fondements du Deep Learning & Géométrie des Représentations

> **Date** : 27 juillet 2026  
> **Thèmes** : Modèles linéaires vs réseaux profonds, Rétropropagation, Expressivité, Métriques de similarité (CKA) et Hypothèse Platonicienne.  
> **Documents disponibles** :
> - 📄 **[Lire les notes complètes en PDF](eeml-2026-day1-foundations.pdf)** *(16 pages, lisible directement sur GitHub)*
> - 📝 **[Document source Word éditable](EEML_2026_Jour1_Notes.docx)**

---

## 🎯 Vue d'ensemble en un coup d'œil

Cette première journée pose les bases théoriques et géométriques indispensables pour comprendre l'apprentissage profond moderne :

### 1. Des modèles linéaires aux réseaux de neurones profonds
* **Le problème XOR et la non-séparabilité** : Pourquoi un hyperplan unique échoue et comment l'empilement de couches cachées non-linéaires tord l'espace géométrique pour rendre les classes linéairement séparables.
* **Du Feature Engineering au Representation Learning** : Le passage historique des descripteurs forgés à la main (SIFT, HOG) aux représentations hiérarchiques apprises de bout en bout (*end-to-end*).
* **Rétropropagation & Calcul matriciel** : Dérivation de la règle de dérivation en chaîne (*chain rule*) pour le calcul automatique des gradients et passage à l'échelle via le calcul vectorisé sur GPU.
* **Capacité & Expressivité** : Théorème d'approximation universelle (Cybenko, Hornik) : pourquoi la profondeur offre une efficacité de représentation exponentielle par rapport à la simple largeur.
* **Le problème du gradient qui s'annule (*Vanishing Gradient*)** : Analyse mathématique de la décomposition des gradients $\prod W_l \sigma'$, rôle des fonctions d'activation (passage de la sigmoïde à ReLU), initialisations adaptées (He, Xavier) et connexions résiduelles (ResNet).

### 2. Géométrie des représentations neuronales
* **Espaces d'embeddings et structure latente** : Lecture géométrique de l'espace latent en tant que variété riemannienne et nuage de points.
* **Comparer deux réseaux neuronaux** : Pourquoi comparer les poids directement n'a pas de sens (problème des permutations et rotations) et quelles métriques invariantes employer :
  - **CKA (Centered Kernel Alignment)** : Alignement de noyaux pour comparer des représentations neuronales d'architectures différentes.
  - **Métrique par régression (Linear Probing)** et **MKNN (Mutual $k$-Nearest Neighbors)**.
* **L'Hypothèse Platonicienne de la représentation** : Les différents modèles d'IA (vision, langage, multimodal) convergent-ils vers une seule et même structure géométrique sous-jacente du monde réel à mesure qu'ils gagnent en échelle ?

---

## 💡 Formule & Intuition clé : CKA (Centered Kernel Alignment)

Pour deux matrices de représentations $X \in \mathbb{R}^{n \times d_1}$ et $Y \in \mathbb{R}^{n \times d_2}$ calculées sur $n$ mêmes exemples :

$$\text{CKA}(K, L) = \frac{\text{HSIC}(K, L)}{\sqrt{\text{HSIC}(K, K) \cdot \text{HSIC}(L, L)}}$$

où $K = X X^\top$, $L = Y Y^\top$ et $\text{HSIC}$ est le critère d'indépendance de Hilbert-Schmidt centré. Cette métrique est invariante aux rotations orthogonales et aux changements d'échelle isotropes, permettant d'aligner deux réseaux aux architectures dissemblables.

---

📖 **Pour approfondir les démonstrations et développements mathématiques :** consultez **[eeml-2026-day1-foundations.pdf](eeml-2026-day1-foundations.pdf)**.
