# EEML 2026 — Journal d'Apprentissage & Notes Techniques

<div align="center">

![EEML 2026](https://img.shields.io/badge/Summer_School-EEML_2026-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Complete-success?style=for-the-badge)
![Language](https://img.shields.io/badge/Language-Français-orange?style=for-the-badge)
![Format](https://img.shields.io/badge/Format-PDF_%2B_Markdown-purple?style=for-the-badge)

**Restitution structurée et approfondie des cours de l'Eastern European Machine Learning Summer School (Cetinje, Monténégro — 27 juillet au 1er août 2026)**

</div>

---

## 📌 À propos de ce recueil

Ce dépôt rassemble mes notes personnelles et mes synthèses techniques rédigées à l'occasion de l'école d'été **EEML 2026**, suivie intégralement à distance depuis le Bénin en tant qu'étudiant en deuxième année de licence à l'**IFRI** (*Institut de Formation et de Recherche en Informatique*, parcours Intelligence Artificielle).

Plutôt que de conserver de simples transcriptions brutes, j'ai entrepris de réécrire, restructurer et clarifier l'ensemble des enseignements avec un fil conducteur constant :

> **« Si je ne peux pas l'expliquer avec mes propres mots, c'est que je ne l'ai pas encore compris. »**

Tous les documents sont disponibles au format **PDF vectoriel haute qualité** (consultables directement dans le navigateur via GitHub) et accompagnés de **fiches de synthèse Markdown** pour un aperçu instantané.

---

## 🚀 Navigation & Modules du cours

| Module | Thématiques abordées | Intervenants clés | Fiche de synthèse | Document complet |
| :--- | :--- | :--- | :---: | :---: |
| **01. Fondements & Représentations** | Problème XOR, Rétropropagation, Capacité, Métriques CKA & Hypothèse Platonicienne | Équipe EEML | [📖 Lire la fiche](01-foundations-and-representations/README.md) | [📄 PDF (16 p.)](01-foundations-and-representations/eeml-2026-day1-foundations.pdf) |
| **02. Reinforcement Learning** | MDP, Bellman, PPO, GRPO (DeepSeek-R1), Statistics Upside Down (Set Transformer++) | Kyunghyun Cho (NYU), Miruna Pislar (DeepMind) | [📖 Lire la fiche](02-reinforcement-learning/README.md) | [📄 PDF (13 p.)](02-reinforcement-learning/eeml-2026-day2-rl.pdf) |
| **03. Contexte Long & Continual Learning** | Attention Sinks, RoPE (Gemma), Oubli catastrophique (EWC), Notions de Venture Capital | Federico Barbara, Claire Lyle, Razvan Pascanu | [📖 Lire la fiche](03-long-context-and-continual-learning/README.md) | [📄 PDF (13 p.)](03-long-context-and-continual-learning/eeml-2026-day3-llm-continual.pdf) |
| **04. HPC & IA pour la Science** | Calcul haute performance, Transcriptomique à cellule unique, LLM & Assistants de preuve (Lean 4) | Maria Brbić (EPFL), Matia Tapušković (Oxford) | [📖 Lire la fiche](04-hpc-and-ai-for-science/README.md) | [📄 PDF (11 p.)](04-hpc-and-ai-for-science/eeml-2026-day4-science-hpc.pdf) |
| **05. Efficient ML & Quantification** | Bitter Lesson, Élagage optimal (OBS), Algorithme GPTQ (INT4/INT3), Réseaux de comorbidité | Dan Alistarh (IST Austria / Neural Magic) | [📖 Lire la fiche](05-efficient-ml-and-quantization/README.md) | [📄 PDF (15 p.)](05-efficient-ml-and-quantization/eeml-2026-day5-efficient-ml.pdf) |
| **06. Geometric DL & Éthique** | Programme d'Erlangen, Invariance/Équivariance, Transformers comme GNNs, Éthique critique de l'IA | Petar Veličković (DeepMind), Dorothy Chou, Magd | [📖 Lire la fiche](06-geometric-dl-and-ethics/README.md) | [📄 PDF (15 p.)](06-geometric-dl-and-ethics/eeml-2026-day6-geometric-dl-ethics.pdf) |
| **Synthèse & Conclusion** | Préface, 3 fils conducteurs transversaux & Bilan réflexif de l'apprentissage | Auteur | [📖 Lire la fiche](final-summary/README.md) | [📄 PDF (5 p.)](final-summary/eeml-2026-final-summary.pdf) |

📚 **Vous souhaitez lire l'intégralité du recueil d'un seul bloc ?**  
👉 **[Télécharger ou consulter le recueil complet des Notes Techniques (88 pages)](EEML_2026_Technical_Notes_Full.pdf)**

---

## ⚡ Parcours rapide selon vos centres d'intérêt

- 🔬 **Vous travaillez sur les modèles de raisonnement et l'alignement (RL / LLM) ?**  
  Consultez le [Module 02](02-reinforcement-learning/README.md) pour les détails sur **PPO, GRPO et DeepSeek-R1**, ainsi que l'estimation statistique apprise par réseaux de neurones.
- 🦙 **Vous vous intéressez à l'extension de contexte dans les Transformers ?**  
  Rendez-vous dans le [Module 03](03-long-context-and-continual-learning/README.md) pour comprendre la géométrie des encodages **RoPE**, le problème des **Attention Sinks** et les méthodes pour contrer l'oubli catastrophique.
- ⚡ **Vous cherchez à déployer des LLMs sur du matériel contraint ?**  
  Le [Module 05](05-efficient-ml-and-quantization/README.md) détaille l'algorithme **GPTQ**, la dérivation analytique de Taylor d'ordre 2 pour l'élagage optimal (*Optimal Brain Surgeon*) et la compression en INT4.
- 📐 **Vous êtes passionné de mathématiques et de géométrie unifiée ?**  
  Le [Module 06](06-geometric-dl-and-ethics/README.md) vous montre comment le **Geometric Deep Learning** unifie les CNN, GNN et Transformers sous le prisme des symétries de groupes.

---

## 📂 Organisation du dépôt

```text
eeml-2026-learning-journal/
│
├── README.md                                  # Page d'accueil & vue d'ensemble
├── EEML_2026_Technical_Notes_Full.pdf         # Recueil complet consolidé (88 pages)
│
├── 01-foundations-and-representations/        # Fondements du deep learning & CKA
│   ├── README.md
│   ├── eeml-2026-day1-foundations.pdf
│   └── EEML_2026_Jour1_Notes.docx
│
├── 02-reinforcement-learning/                 # RL moderne, PPO, GRPO & Statistics Upside Down
│   ├── README.md
│   ├── eeml-2026-day2-rl.pdf
│   └── EEML_2026_Jour2_Notes.docx
│
├── 03-long-context-and-continual-learning/    # Contexte long (RoPE), VC & Continual Learning
│   ├── README.md
│   ├── eeml-2026-day3-llm-continual.pdf
│   └── EEML_2026_Jour3_Notes.docx
│
├── 04-hpc-and-ai-for-science/                 # Supercalculateurs, biologie cellulaire & maths formelles
│   ├── README.md
│   ├── eeml-2026-day4-science-hpc.pdf
│   └── EEML_2026_Jour4_Compte-rendu.docx
│
├── 05-efficient-ml-and-quantization/          # Élagage optimal, quantification GPTQ & santé
│   ├── README.md
│   ├── eeml-2026-day5-efficient-ml.pdf
│   └── EEML_2026_Jour5_Notes.docx
│
├── 06-geometric-dl-and-ethics/                # Geometric Deep Learning & Éthique de l'IA
│   ├── README.md
│   ├── eeml-2026-day6-geometric-dl-ethics.pdf
│   └── EEML_2026_Jour6_Notes.docx
│
└── final-summary/                             # Préface, fils conducteurs transversaux & conclusion
    ├── README.md
    ├── eeml-2026-final-summary.pdf
    └── EEML_2026_Technical_Notes_Learning_Journal.docx
```

---

## 📝 Avertissement légal & Citation

Ce dépôt est une initiative étudiante personnelle de restitution pédagogique. Il ne s'agit pas des supports de cours officiels de l'organisation de l'EEML, mais d'une réécriture indépendante à visée d'apprentissage personnel et de partage communautaire.

Si ce travail vous est utile, n'hésitez pas à laisser une ⭐ sur ce dépôt !
