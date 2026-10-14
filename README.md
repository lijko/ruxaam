# RUXAAM — Revue UX Accessibilité (mobile)

**FR** — Outil HTML autonome (un seul fichier, hors ligne) qui aide à **préparer et prioriser un audit d'accessibilité d'application mobile**, avant l'audit complet. Il croise :

- **59 critères essentiels du RAAM 1.1** (référentiel du SIP, Luxembourg), évalués un à un (conforme, non conforme, non testé, non applicable), qui donnent un **taux de conformité** ;
- **une lecture UX qualitative** (principes POUR de WCAG et heuristiques d'utilisabilité), **exclue du taux**.

Trois types d'audit : audit rapide, fonctionnalité primaire, scénario. Exports CSV, Jira, JSON et PDF.

RUXAAM n'est **pas un audit de conformité** et ne produit aucune déclaration d'accessibilité : c'est un outil de pré-diagnostic, qui complète l'audit d'un expert.

**EN** — Standalone, offline, single-file HTML tool to **prepare and prioritise a mobile accessibility audit**. It combines **59 essential RAAM 1.1 criteria** (Luxembourg's mobile accessibility standard; compliance rate) with a **qualitative UX layer** (WCAG POUR principles and usability heuristics; excluded from the rate). It is **not a compliance audit**.

## Utilisation
Ouvrir `ruxaam.html` dans un navigateur. Aucune installation, aucun serveur, aucun appel réseau. Les données restent dans le navigateur ; l'état s'exporte et s'importe en JSON.

## Contenu du dépôt
| Fichier | Rôle |
|---|---|
| `ruxaam.html` | l'outil |
| `DOCUMENTATION.md` | sélection des critères, règle « si présent », gravités, limites, liste des 59 critères |
| `LICENSE` | EUPL-1.2 |
| `README.md` | ce fichier |

## Licence et attributions
- **Code, textes d'impact et de test, thèmes, gravités et bonnes pratiques de RUXAAM** : © 2026 Bertrand Kempf, [EUPL-1.2](LICENSE).
- **Critères du RAAM 1.1** (intitulés, niveaux, références WCAG et EN 301 549) : © Service information et presse (SIP), Luxembourg, [CC BY 3.0 LU](https://creativecommons.org/licenses/by/3.0/lu/), reproduits sans modification. Le RAAM est lui-même dérivé de documents de la DINUM (RGAA). Source : <https://github.com/accessibility-luxembourg/ReferentielAccessibiliteMobile>. Ces éléments restent sous leur licence d'origine ; l'EUPL ne s'y applique pas.
  Modifications de RUXAAM : sélection de 59 critères, regroupement par thèmes, gravités, textes d'impact et de test.
- **jsPDF 2.5.1** (embarqué dans `ruxaam.html`) : © 2010-2021 James Hall et contributeurs, licence MIT. Les en-têtes de copyright de la bibliothèque et de ses greffons sont conservés dans le fichier.
- **WCAG 2.1** : © W3C. Les numéros et intitulés des critères de succès viennent du RAAM ; les textes de RUXAAM sont originaux.
- **Heuristiques d'utilisabilité** : Nielsen Norman Group, <https://www.nngroup.com/articles/ten-usability-heuristics/> (questions reformulées par RUXAAM, texte d'origine non reproduit).
- **Échelle de gravité** : noms des quatre niveaux inspirés de l'échelle d'impact de Deque (axe-core, MPL-2.0), aucun code repris.

RUXAAM n'est ni approuvé ni certifié par le SIP, l'OSAPS, le W3C ou Deque Systems.

## Contribuer
Ouvrez une issue avant une évolution importante. Les critères officiels (numéro, intitulé, niveau) ne se modifient pas. L'outil doit rester accessible (clavier, contrastes, lecteurs d'écran) et sans dépendance réseau. N'ajoutez aucune donnée confidentielle.
