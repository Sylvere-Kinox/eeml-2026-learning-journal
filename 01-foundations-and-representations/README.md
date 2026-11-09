# Jour 1 — Fondements du Deep Learning et géométrie des représentations

Date : 27 juillet 2026  
Thèmes : Modèles linéaires vs réseaux profonds, rétropropagation, expressivité, métriques de similarité (CKA) et hypothèse platonicienne.

Documents :
- [Notes complètes (PDF)](eeml-2026-day1-foundations.pdf)
- [Document source Word](EEML_2026_Jour1_Notes.docx)

## Synthèse

### 1. Des modèles linéaires aux réseaux de neurones profonds
- **Problème XOR et séparabilité linéaire** : limites d'un hyperplan unique et transformation d'espace induite par des couches cachées non-linéaires.
- **Du feature engineering au representation learning** : passage des descripteurs construits manuellement aux représentations hiérarchiques apprises de bout en bout.
- **Rétropropagation** : calcul matriciel des gradients par dérivation en chaîne et passage à l'échelle sur GPU.
- **Capacité et expressivité** : théorème d'approximation universelle et efficacité de la profondeur par rapport à la largeur.
- **Problème du gradient qui s'annule** : analyse de la décomposition des gradients, rôle des fonctions d'activation (ReLU), initialisations (He, Xavier) et connexions résiduelles (ResNet).

### 2. Géométrie des représentations neuronales
- **Espaces latents** : lecture géométrique des espaces d'activation.
- **Comparaison de représentations** : limites de la comparaison directe des poids (invariance par permutation et rotation).
  - CKA (Centered Kernel Alignment) : mesure d'alignement de noyaux pour comparer des réseaux de topologies différentes.
  - Linear probing et métriques par plus proches voisins (MKNN).
- **Hypothèse platonicienne de la représentation** : convergence des modèles vers des structures géométriques partagées avec l'augmentation d'échelle et la multimodalité.

## Formule clé : CKA (Centered Kernel Alignment)

Pour deux matrices de représentations $X \in \mathbb{R}^{n \times d_1}$ et $Y \in \mathbb{R}^{n \times d_2}$ calculées sur les $n$ mêmes exemples :

$$\text{CKA}(K, L) = \frac{\text{HSIC}(K, L)}{\sqrt{\text{HSIC}(K, K) \cdot \text{HSIC}(L, L)}}$$

où $K = X X^\top$, $L = Y Y^\top$ et $\text{HSIC}$ désigne le critère d'indépendance de Hilbert-Schmidt centré.
