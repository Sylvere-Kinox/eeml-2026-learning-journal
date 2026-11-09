# Jour 5 — Apprentissage Efficace, Quantification (GPTQ) & IA pour la Santé

> **Date** : 31 juillet 2026  
> **Intervenants principaux** : Dan Alistarh (IST Austria / Neural Magic), Elma Dervishi, Suad Glass (ANT)  
> **Thèmes** : Bitter Lesson, Élagage optimal (OBS), Algorithme GPTQ, Réseaux de comorbidité médicale.  
> **Documents disponibles** :
> - 📄 **[Lire les notes complètes en PDF](eeml-2026-day5-efficient-ml.pdf)** *(15 pages, lisible directement sur GitHub)*
> - 📝 **[Document source Word éditable](EEML_2026_Jour5_Notes.docx)**

---

## 🎯 Vue d'ensemble en un coup d'œil

### 1. Apprentissage efficace en calcul & Compression de modèles (Dan Alistarh)
* **La « Bitter Lesson » de Rich Sutton** : Les méthodes tirant parti du passage à l'échelle et du calcul brut l'emportent toujours sur les heuristiques artisanales humaines — mais ce constat crée un mur énergétique et matériel insoutenable.
* **Fondements mathématiques de l'élagage (*Pruning*)** :
  - Pourquoi supprimer les plus petits poids en valeur absolue (*magnitude pruning*) est sous-optimal.
  - Dérivation taylorienne d'ordre 2 de la fonction de perte : l'impact de la suppression d'un paramètre $w_q$ dépend de l'inverse de la matrice hessienne $H^{-1}$ :
    $$L_q = \frac{1}{2} \frac{w_q^2}{[H^{-1}]_{qq}}$$
  - **Optimal Brain Surgeon (OBS)** : Compensation analytique des poids restants lors de la suppression de chaque paramètre :
    $$\delta \mathbf{w} = - \frac{w_q}{[H^{-1}]_{qq}} H^{-1} \mathbf{e}_q$$
* **L'algorithme de quantification GPTQ (General Post-Training Quantization)** :
  - Passage à l'échelle pour des modèles de plusieurs dizaines ou centaines de milliards de paramètres.
  - Inversion et régularisation de Cholesky du Hessien empirique calculé sur un petit ensemble de calibration ($H = 2 X X^\top + \lambda I$).
  - Quantification colonne par colonne par blocs avec propagation matricielle paresseuse (*lazy batch update*).
  - Résultats remarquables : compression de modèles de FP16 à INT4 (voire INT3) avec une perplexité quasiment identique à l'original et une exécution ultra-rapide sur GPU grand public.

### 2. IA pour la médecine & Trajectoires de santé
* **Modélisation des réseaux de comorbidité** : Cartographie des relations causales et corrélations entre pathologies à partir de dossiers médicaux électroniques longitudinaux.
* **Repositionnement de molécules thérapeutiques** : Utilisation de réseaux de neurones sur graphes hétérogènes (gènes, protéines, molécules, phénotypes) pour identifier de nouvelles indications thérapeutiques à des médicaments déjà approuvés par les autorités sanitaires.

### 3. Vitrine de recherche régionale & Engagement
* Études de cas appliquées dans les Balkans : détection d'anomalies sur signaux biomédicaux (fibrillation auriculaire) et modélisation spectrale de graphes orientés acycliques (DAG).
* Rôle sociétal et démonstration de l'impact du bénévolat scientifique pour bâtir des passerelles éducatives durables (association ANT).

---

## 💡 Formule clé : La mise à jour GPTQ

Lors de la quantification de la colonne $q$ de la matrice de poids vers sa valeur discrète la plus proche $Q(w_q)$, le vecteur de correction appliqué aux colonnes non encore quantifiées $w_{:, i}$ ($i > q$) est donné par :

$$\Delta \mathbf{w}_{:, >q} = - \frac{w_{:, q} - Q(w_{:, q})}{[H^{-1}]_{qq}} \cdot [H^{-1}]_{q, >q}$$

Cette formule élégante garantit que l'erreur de quantification commise sur un groupe de poids est instantanément compensée par les poids voisins avant que ces derniers ne soient eux-mêmes quantifiés.

---

📖 **Pour approfondir les démonstrations de Taylor d'ordre 2 et les benchmarks GPTQ :** consultez **[eeml-2026-day5-efficient-ml.pdf](eeml-2026-day5-efficient-ml.pdf)**.
