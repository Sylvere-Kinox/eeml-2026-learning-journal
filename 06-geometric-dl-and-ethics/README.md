# Jour 6 — Apprentissage Profond Géométrique (GDL) & Éthique de l'IA

> **Date** : 1er août 2026 (Dernière journée de l'école d'été)  
> **Intervenants principaux** : Petar Veličković (Google DeepMind), Dorothy Chou (Google DeepMind), Magd, Mariana Neshovska  
> **Thèmes** : Programme d'Erlangen, Invariance & Équivariance, GNN & Transformers, Réécriture des trajectoires, Éthique critique de l'IA.  
> **Documents disponibles** :
> - 📄 **[Lire les notes complètes en PDF](eeml-2026-day6-geometric-dl-ethics.pdf)** *(15 pages, lisible directement sur GitHub)*
> - 📝 **[Document source Word éditable](EEML_2026_Jour6_Notes.docx)**

---

## 🎯 Vue d'ensemble en un coup d'œil

### 1. Geometric Deep Learning — GDL (Petar Veličković, DeepMind)
* **Le Programme d'Erlangen transposé au Deep Learning** : De même que Felix Klein a unifié la géométrie au XIXe siècle à travers la théorie des groupes de symétries, le GDL unifie toutes les architectures neuronales modernes à travers leurs symétries sous-jacentes.
* **Le plan directeur : Invariance et Équivariance** :
  - **Équivariance** sous l'action d'un groupe $G$ : $f(\rho(g) \cdot x) = \rho'(g) \cdot f(x)$ (les transformations en entrée se répercutent de façon prévisible en sortie).
  - **Invariance** : $f(\rho(g) \cdot x) = f(x)$ (la sortie ne change pas quelle que soit la transformation appliquée en entrée).
* **La taxonomie des 5 domaines géométriques (les 5 Gs)** :
  1. **Grilles régulières ($\mathbb{Z}^2$)** : La symétrie par translation mène canoniquement aux convolutions (**CNN**).
  2. **Graphes et ensembles non ordonnés** : La symétrie par permutation des nœuds $\mathcal{S}_n$ impose le paradigme du passage de messages (**Message Passing Neural Networks - MPNN**).
  3. **Les Transformers vus comme des GNNs** : Démonstration mathématique qu'un Transformer est un GNN opérant sur un graphe complet où la matrice d'adjacence est calculée dynamiquement via le mécanisme de Softmax attention.
  4. **Groupes et espaces sphériques ($\text{SO}(3)$)** : Architectures équivariantes pour la modélisation moléculaire 3D et les dynamiques de particules.
  5. **Variétés riemanniennes & Fibrés de jauge** : Théorie des jauges, transport parallèle et applications biomoléculaires (fondements géométriques d'**AlphaFold**).

### 2. Réécrire les règles de sa carrière en IA (Dorothy Chou, DeepMind)
* Déconstruction des 3 mythes académiques traditionnels (linéarité des carrières, isolement du chercheur, primauté du prestige institutionnel).
* Stratégies d'impact pour les chercheurs et ingénieurs issus de régions sous-représentées (comme l'Afrique ou l'Europe de l'Est).

### 3. La réalité du travail en éthique et impact sociétal de l'IA (Magd)
* **Distinguer l'éthique de l'IA de l'ingénierie de sécurité (*AI Safety*)** : Pourquoi l'alignement technique ne résout pas les questions de redistribution du pouvoir, d'inégalités économiques et d'impacts environnementaux.
* **Le coût personnel et institutionnel** : Les effets *Sagan* et *Gebru* dans les carrières des scientifiques alertant sur les dérives sociétales.
* **L'absence de vérité terrain (*ground truth*)** : Pourquoi les méthodes supervisées classiques échouent à modéliser des concepts politiques ou sociétaux fondamentalement contestés.

---

## 💡 Théorème & Principe unificateur : L'Attention comme Message Passing

Dans un réseau de neurones sur graphe avec passage de messages (MPNN) :

$$\mathbf{h}_i^{(t+1)} = \phi \left( \mathbf{h}_i^{(t)}, \bigoplus_{j \in \mathcal{N}(i)} \psi(\mathbf{h}_i^{(t)}, \mathbf{h}_j^{(t)}) \right)$$

Lorsque le voisinage $\mathcal{N}(i)$ correspond à l'ensemble de tous les tokens de la séquence ($V$), que la fonction de message $\psi$ calcule les paires Query-Key pondérées par Value, et que l'agrégateur $\bigoplus$ est une somme pondérée par Softmax, **on retrouve rigoureusement le bloc d'auto-attention du Transformer**.

---

📖 **Pour approfondir les dérivations d'équivariance de jauge et les fondements du GDL :** consultez **[eeml-2026-day6-geometric-dl-ethics.pdf](eeml-2026-day6-geometric-dl-ethics.pdf)**.
