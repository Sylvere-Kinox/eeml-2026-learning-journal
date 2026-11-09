# Jour 4 — Calcul Haute Performance, IA pour la Biomédecine & Mathématiques Formelles

> **Date** : 30 juillet 2026  
> **Intervenants principaux** : Maria Brbić (EPFL), Matia Tapušković (Université d'Oxford), NCC Monténégro / EuroCC, UiPath  
> **Thèmes** : Supercalculateurs & EuroHPC, Transcriptomique & Morphologie cellulaire, LLMs & Assistants de preuve (Lean).  
> **Documents disponibles** :
> - 📄 **[Lire les notes complètes en PDF](eeml-2026-day4-science-hpc.pdf)** *(11 pages, lisible directement sur GitHub)*
> - 📝 **[Document source Word éditable](EEML_2026_Jour4_Compte-rendu.docx)**

---

## 🎯 Vue d'ensemble en un coup d'œil

### 1. Calcul Haute Performance (HPC) & Infrastructure EuroHPC
* Rôle des centres de compétences nationaux (NCC) et du réseau EuroCC pour démocratiser l'accès aux supercalculateurs européens (LUMI, Leonardo, MareNostrum) pour la recherche en IA.
* Gestion des contraintes d'infrastructure : parallélisme de données (DDP), parallélisme de tenseurs (TP), parallélisme de pipeline (PP) et optimisations d'entrées/sorties (I/O).

### 2. L'IA au service de la biomédecine (Maria Brbić, EPFL)
* **La révolution des données omiques** : Analyse à l'échelle de la cellule unique (*single-cell RNA sequencing*).
* **Aligner transcriptome et morphologie cellulaire** : Prédire les profils d'expression génique directement à partir d'images microscopiques de tissus (et inversement).
* **Prédiction de réponse aux perturbations cellulaires** : Utiliser des modèles génératifs et des représentations latentes pour prédire l'effet d'une molécule médicamenteuse ou d'une inactivation génétique par CRISPR sans réaliser l'expérience en laboratoire humide (*wet lab*).
* **Transfert multimodal avec peu de paires appariées** : Techniques d'alignement d'espaces latents utilisant le transport optimal et les métriques de géométrie d'espace.

### 3. L'apprentissage automatique au service des mathématiques (Matia Tapušković, Oxford)
* **Pourquoi les LLMs classiques peinent en mathématiques pures** : Absence de vérité terrain formelle dans la génération autoregressive standard et propension aux erreurs d'inférence logique subtiles.
* **Le pont vers la vérification formelle (Lean 4, Isabelle, Coq)** :
  - Utiliser les modèles de langage comme des moteurs de génération de tactiques de preuve (*autoformalization*).
  - Boucle de rétroaction fermée : le prouveur formel fournit un signal de récompense binaire infaillible (preuve acceptée ou rejetée).
* **Découverte de conjectures et géométrie algébrique** : Utilisation de réseaux de neurones (GNN, Transformers) pour détecter des invariants cachés et guider l'intuition des mathématiciens.

### 4. Automatisation & Agents d'action informatique (UiPath)
* Des modèles de perception d'interface utilisateur (Computer Vision pour UI) aux agents autonomes exécutant des flux de travail complexes à travers des API et des écrans.

---

## 💡 Idée clé : La synergie LLM + Prouveur formel (Lean 4)

L'apprentissage automatique ne remplace pas la rigueur mathématique, il explore l'arbre de recherche combinatoire :

$$\text{LLM (Générateur de tactiques)} \xrightarrow{\text{Propositions}} \text{Vérificateur Lean (Contrôle formel du noyau)} \xrightarrow{\text{Feedback exact}} \text{Mise à jour RL}$$

Cette symbiose élimine les hallucinations mathématiques en s'appuyant sur un vérificateur de type rigoureux basé sur la théorie des types dépendants (calcul des constructions inductives).

---

📖 **Pour approfondir les études de cas biomédicales et les protocoles formels :** consultez **[eeml-2026-day4-science-hpc.pdf](eeml-2026-day4-science-hpc.pdf)**.
