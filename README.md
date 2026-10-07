# PIPETO

Audit de sécurité complet d'un logiciel de contrôle de réacteur nucléaire
volontairement vulnérable : identifier les failles, les exploiter **sans jamais
modifier le code d'origine**, puis les corriger proprement et prouver chaque
correctif par un test unitaire.

Le projet se joue en Purple Team — la partie offensive (Red Team) et la partie
défensive (Blue Team) sont menées par la même équipe, ce qui oblige à comprendre
une faille en profondeur avant de pouvoir la réparer.

> **Epitech · `G-SEC-210` (« pipeto »)** — projet d'équipe mené avec
> [graigware](https://github.com/graigware).
>
> **Mon rôle :** analyse par rétro-ingénierie et exploitation.
>
> Ce dépôt est ma copie personnelle du rendu, publiée comme projet de portfolio.
> Le dépôt d'origine est privé. Le rapport écrit n'est pas inclus ici (il cite des
> éléments du sujet confidentiel) — les preuves du travail restent les correctifs,
> les tests et le code de la librairie récupérée.

---

## Contexte

L'application est un shell de commandes (`pipeto`) pilotant un réacteur : charge de
combustible, pression de refroidissement, puissance, diagnostic, protocole
d'urgence. Elle s'appuie sur une bibliothèque partagée, `libpepito.so`, fournie
**sans code source** — d'où une première phase d'analyse en boîte noire.

## Démarche

1. **Audit Black Box** — le binaire et la bibliothèque uniquement : cartographie des
   commandes, désassemblage, recherche de motifs suspects.
2. **Audit White Box** — une fois le code source disponible, revue ligne à ligne des
   fonctions sensibles : `check_cooling_pressure`, `set_reactor_power`,
   `load_config`, `run_turbine`, `unlock_secret_mode`, etc.
3. **Exploitation** — chaque faille est prouvée par un script, sans toucher au code
   d'origine.
4. **Remédiation** — un patch par faille, un test unitaire par correctif.

## Contenu du dépôt

| Dossier | Contenu |
|---|---|
| `Pipeto/Pipeto/` | Le shell vulnérable : `src/main.c`, `src/my_console.c`, `src/utils.c` et `src/commands/` (17 commandes) |
| `libpipeto/` | Les fonctions de `libpepito.so` reconstituées à partir de la bibliothèque fournie (rétro-ingénierie) |
| `patch/` | 17 correctifs au format `.patch` — un par faille, plus les ajustements de `Makefile`, `main` et `utils` |
| `tests/` | 10 tests unitaires validant les correctifs |

## Appliquer les correctifs

```bash
# depuis la racine du dépôt
git apply patch/<nom_du_fichier>.patch
```

Pour lancer le binaire vulnérable tel quel :

```bash
chmod 655 ./Pipeto/Pipeto/pipeto
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PWD/Pipeto/Pipeto
./Pipeto/Pipeto/pipeto
```

## Classes de vulnérabilités traitées

Débordements de pile et de tas, chaînes de format, use-after-free, écritures hors
bornes et secret caché dans le binaire — chacune documentée par sa gravité, son
impact, sa preuve d'exploitation et sa correction.
