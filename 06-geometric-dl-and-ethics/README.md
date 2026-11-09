# Jour 6 — Deep Learning géométrique et éthique de l'IA

Date : 1er août 2026  
Intervenants : Petar Veličković (Google DeepMind), Dorothy Chou (Google DeepMind), Magd, Mariana Neshovska  
Thèmes : Programme d'Erlangen, invariance et équivariance, GNN et Transformers, carrières en recherche, éthique critique de l'IA.

Documents :
- [Notes complètes (PDF)](eeml-2026-day6-geometric-dl-ethics.pdf)
- [Document source Word](EEML_2026_Jour6_Notes.docx)

## Synthèse

### 1. Geometric Deep Learning — GDL (Petar Veličković)
- **Programme d'Erlangen pour l'apprentissage profond** : unification des architectures neuronales à travers les groupes de symétries des domaines sous-jacents.
- **Principes d'équivariance et d'invariance** sous l'action d'un groupe $G$ :
  - Équivariance : $f(\rho(g) \cdot x) = \rho'(g) \cdot f(x)$
  - Invariance : $f(\rho(g) \cdot x) = f(x)$
- **Taxonomie des domaines géométriques (les 5 Gs)** :
  - Grilles régulières : translation -> Convolutions (CNN).
  - Graphes : invariance par permutation des nœuds $\mathcal{S}_n$ -> Message Passing Neural Networks (MPNN).
  - Transformers comme GNN : équivalence entre auto-attention et passage de messages sur un graphe complet avec arêtes pondérées dynamiquement.
  - Groupes et sphères $\text{SO}(3)$ : architectures équivariantes pour la chimie et les données 3D.
  - Variétés riemanniennes et fibrés de jauge : transport parallèle et géométrie sur surfaces (AlphaFold).

### 2. Écosystèmes et carrières en recherche (Dorothy Chou)
- Analyse des parcours non linéaires en recherche en intelligence artificielle.
- Développement de communautés de recherche dans les régions sous-représentées (exemple d'AI Albania).

### 3. Éthique et impacts sociétaux de l'IA (Magd)
- Distinction entre éthique de l'IA (analyse des rapports de pouvoir, impacts économiques et environnementaux) et ingénierie de sécurité technique (*safety/alignment*).
- Spécificités de l'évaluation sociétale : absence de vérité de terrain (*ground truth*) sur les questions politiques et sociales contestées.

## Principe d'unification : L'Attention comme Message Passing

Dans un réseau sur graphe avec passage de messages :

$$\mathbf{h}_i^{(t+1)} = \phi \left( \mathbf{h}_i^{(t)}, \bigoplus_{j \in \mathcal{N}(i)} \psi(\mathbf{h}_i^{(t)}, \mathbf{h}_j^{(t)}) \right)$$

Lorsque le voisinage $\mathcal{N}(i)$ est l'ensemble complet des jetons et que l'agrégateur est une somme pondérée par l'attention Softmax, l'opération coïncide avec le bloc d'auto-attention des Transformers.
