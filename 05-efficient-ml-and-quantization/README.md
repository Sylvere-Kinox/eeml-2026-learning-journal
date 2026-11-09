# Jour 5 — Apprentissage efficace, compression de modèles et IA médicale

Date : 31 juillet 2026  
Intervenants : Dan Alistarh (IST Austria / Neural Magic), Elma Dervishi, Suad Glass (ANT)  
Thèmes : Élagage de réseaux (Optimal Brain Surgeon), quantification post-entraînement (GPTQ), réseaux de comorbidité médicale.

Documents :
- [Notes complètes (PDF)](eeml-2026-day5-efficient-ml.pdf)
- [Document source Word](EEML_2026_Jour5_Notes.docx)

## Synthèse

### 1. Compression et passage à l'échelle (Dan Alistarh)
- **Coût computationnel et Bitter Lesson** : limites pratiques de l'augmentation continue de la taille des modèles.
- **Fondements mathématiques de l'élagage (Pruning)** :
  - Limites de la suppression basée uniquement sur l'amplitude des poids (*magnitude pruning*).
  - Développement de Taylor d'ordre 2 de la fonction de perte et formulation de l'Optimal Brain Surgeon (OBS) :
    $$L_q = \frac{1}{2} \frac{w_q^2}{[H^{-1}]_{qq}}$$
  - Compensation des poids restants après élimination d'un paramètre :
    $$\delta \mathbf{w} = - \frac{w_q}{[H^{-1}]_{qq}} H^{-1} \mathbf{e}_q$$
- **Algorithme GPTQ** :
  - Adaptation de la méthode OBS aux modèles de grande taille via une décomposition de Cholesky du Hessien empirique régularisé ($H = 2 X X^\top + \lambda I$).
  - Quantification colonne par colonne par blocs avec mise à jour matricielle par lots.
  - Réduction de la précision de FP16 à INT4/INT3 sans dégradation marquée de la perplexité.

### 2. Applications biomédicales et recherche régionale
- Réseaux de comorbidité : analyse causale et temporelle à partir de données de dossiers de santé longitudinaux.
- Repositionnement de molécules existantes sur de nouvelles cibles thérapeutiques à l'aide de graphes biomoléculaires hétérogènes.
- Analyse spectrale de graphes orientés acycliques (DAG) et détection d'anomalies sur signaux physiologiques.

## Formule clé : Mise à jour des poids dans GPTQ

Lors de la quantification de la colonne $q$ vers $Q(w_q)$, la mise à jour des colonnes restantes $w_{:, i}$ ($i > q$) est :

$$\Delta \mathbf{w}_{:, >q} = - \frac{w_{:, q} - Q(w_{:, q})}{[H^{-1}]_{qq}} \cdot [H^{-1}]_{q, >q}$$
