> **Epitech project — `G-SEC-210` (`pipeto`)**
>
> Built with [graigware](https://github.com/graigware).
> I worked on the reverse-engineering and exploitation analysis.
>
> This is my own copy of the assignment repository, published here as a
> portfolio piece. The original repository is private.

---

# 🔐 PIPETO - Reverse Engineering & Binary Exploitation

## 📘 Introduction

**PIPETO** est un projet de cybersécurité complet centré sur l’audit et l’exploitation d’un binaire compilé. Il simule une véritable opération Purple Team — combinant les approches offensives (Red Team) et défensives (Blue Team).

Ce projet plonge les étudiants dans les réalités de l’analyse binaire, de l’exploitation de vulnérabilités et de la sécurisation de code, dans un contexte à haute pression, proche du réel.

---

## 🎯 Mission Context

Vous êtes **Application Security Engineer** chez **The Stone Corporation**, une société de cybersécurité de haut niveau. Votre équipe est mandatée par le gouvernement de la République d'Obsidienne pour sécuriser le logiciel de contrôle d'une centrale nucléaire.

Le logiciel est fonctionnel, mais dépourvu de protections modernes. Les renseignements suggèrent une attaque numérique imminente, orchestrée par **G.O.L.E.M.** (Global Offensive for Logical Exploitation and Manipulation), une organisation d’IA renégate spécialisée dans le sabotage cybernétique.

Votre rôle ne se limite pas à l’analyse : vous devez anticiper, contrer et sécuriser face à un adversaire redoutable. Chaque bug découvert, chaque correctif appliqué, est une victoire pour la stabilité nationale.

---

## 🧠 Purple Team

| Rôle         | Objectif                                                              |
|--------------|-----------------------------------------------------------------------|
| 🔴 Red Team  | Simuler les attaques, identifier les vulnérabilités, extraire des données critiques |
| 🔵 Blue Team | Corriger les vulnérabilités, valider les corrections avec tests et patchs |
| 🟣 Purple Team | Travailler en synergie pour assurer une couverture sécuritaire optimale |

---

## 📦 Objectifs du Projet

- ✅ Réaliser un audit Black Box (binaire + librairie dynamique uniquement).
- ✅ Réaliser un audit White Box (accès complet au code source).
- ✅ Identifier, classifier et documenter toutes les vulnérabilités découvertes.
- ✅ Exploiter les failles **sans modifier le code original**.
- ✅ Corriger les vulnérabilités en C, de façon sécurisée.
- ✅ Écrire des tests unitaires pour valider chaque correctif.
- ✅ Générer un fichier `.patch` par correction.
- ✅ Rédiger un rapport de vulnérabilités clair et professionnel.
- ✅ Défendre le projet lors d’une présentation simulée devant un comité de sécurité.

---

## 🧰 Environnement & Outils

- **Langage** : C
- **Système** : Linux
- **Commande d’exécution** :

```bash
chmod 655 ./pipeto
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PWD
```

## 📝 Template du Rapport

### Faille X, [Nom de la commande vulnérable]
- **Gravité** : [faible / moyenne / élevée / critique]
- **Type** : [Buffer Overflow, Format String, Use-After-Free, etc.]
- **Fichier** : `src/[nom_du_fichier].c`
- **Fonction** : `[nom_de_la_fonction]`
- **Détectée lors de** : [Audit Black Box / Audit White Box]

**Demonstration :**  
[Description technique détaillée de la faille]

**Proof of Concept :**  
[Étapes ou script permettant de reproduire l'exploitation]

**Impact :**  
[Exécution de code à distance, crash, élévation de privilège, etc.]

**Résumé de la correction :**
- [Explication claire de la solution implémentée]
- Fichier patch : `patch/[nom_du_fichier].c.patch`
- Test unitaire : Oui / Non
- Couverture de test : 100% / Partielle

## 📁 Dossier Patch

**Structure du dossier**
patch/
├── faille1.patch
├── faille2.patch
└── faille3.patch

**git apply**

```bash
git apply patch/[nom_fichier].patch
```

## 📁 Dossier libpipeto

Ce dossier contient toutes les fonctions du code source de la librairie **libpepito.so**.
Elles ont été récupérées grâce à l'outil **ghidra** 🐉.
