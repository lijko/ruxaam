# RUXAAM : Revue UX Accessibilité (mobile)

**FR** : Outil HTML autonome (un seul fichier, hors ligne) qui aide à **préparer et prioriser un audit d'accessibilité d'application mobile**, avant l'audit complet. Il croise :

- **52 critères essentiels du RAAM 1.1** (référentiel du SIP, Luxembourg), dont 20 « si présent », évalués un à un (conforme, non conforme, non testé, non applicable), qui donnent un **taux de conformité** ;
- **une lecture UX qualitative** (principes POUR de WCAG et heuristiques d'utilisabilité), **exclue du taux** ;
- **3 bonnes pratiques** hors RAAM (zone tactile, retour ou fermeture, retour du focus), également hors taux.

Trois types d'audit : audit rapide, fonctionnalité primaire, scénario. Exports Excel (liste des critères), CSV (import Jira), JSON et PDF.

- **Protocole de test en 4 étapes** : 1. usage standard, 2. agrandissement, 3. lecteur d'écran (3a contenus et structure, 3b composants, formulaires et annonces), 4. navigation alternative. Chaque critère est rattaché à l'étape où on le constate le plus facilement. Séquence construite par RUXAAM à partir des pratiques décrites par Apple et Android ; ce n'est pas un protocole officiel.
- **Vue « Par étape de test »** : la liste d'un onglet RAAM se range par thème ou par étape, sans effet sur le taux ni les exports.
- **Plateforme** (iOS, Android ou multiplateforme) : un audit = une plateforme ; elle détermine les recommandations et l'étiquette des tickets Jira.
- **Contenu des écrans** : un interrupteur par écran et par type d'élément (CAPTCHA, image complexe, média, tableau, formulaire), plus « Limite de session » pour toute l'application. Un critère « si présent » ne s'affiche que là où l'élément existe ; ailleurs il compte comme NA, sans rien effacer.
- **Écrans testés** : dans un onglet, le panneau « Écrans testés » permet de renommer, d'ajouter ou de supprimer (en deux clics) un écran en cours d'audit. Un ajout ou une suppression repasse l'onglet en brouillon ; un nouvel écran part en NT. L'audit rapide garde au moins 3 écrans. Les tickets Jira déjà créés ne sont pas modifiés.
- **Un écran à la fois** : au-delà de 6 écrans (outil pensé pour l'ordinateur), la liste n'affiche plus que l'écran choisi dans une barre qui reste visible pendant le défilement (avec Précédent / Suivant et le nombre de non-conformités par écran), plus la colonne « Tous » et le statut d'ensemble de l'onglet sur chaque critère.
- **Élément concerné** : pour chaque critère non conforme, la notation `Écran[type "Libellé"] (état)` (expliquée dans l'Aide) désigne l'élément en cause ; l'export Jira la reprend.
- **Formats d'export** : Liste des critères en **Excel (.xlsx)** : une ligne par critère et par onglet, colonnes dimensionnées, ligne d'en-tête figée, filtres, statuts colorés, numéros de critères gardés en texte (« 10.10 » reste 10.10). Tickets Jira en **CSV** (séparateur virgule), à importer dans Jira et non à ouvrir dans Excel. Le téléchargement passe uniquement par le navigateur, sans dépendance à une autre application. 
- **Exports** : jamais de fichier vide ; un message explique pourquoi un export n'a pas lieu. L'outil retient les tickets Jira déjà exportés et ne les exporte pas deux fois (« Tickets Jira : tout réexporter » pour tout reprendre).

RUXAAM n'est **pas un audit de conformité** et ne produit aucune déclaration d'accessibilité : c'est un outil de pré-diagnostic, qui complète l'audit d'un expert.

**EN** : Standalone, offline, single-file HTML tool to **prepare and prioritise a mobile accessibility audit**. It combines **52 essential RAAM 1.1 criteria** (Luxembourg's mobile accessibility standard; compliance rate) with a **qualitative UX layer** (WCAG POUR principles and usability heuristics; excluded from the rate). It offers a 4-step test protocol (standard use, enlargement, screen reader, alternative navigation), a view by test step, per-screen content switches for conditional criteria, an « affected element » field, and Jira export with platform choice and memory of exported tickets. It is **not a compliance audit**.

## Utilisation
Ouvrir `ruxaam.html` dans un navigateur. Aucune installation, aucun serveur, aucun appel réseau. Les données restent dans le navigateur ; l'état s'exporte et s'importe en JSON.

## Contenu du dépôt
| Fichier | Rôle |
|---|---|
| `ruxaam.html` | l'outil |
| `DOCUMENTATION.md` | sélection des critères, règle « si présent », protocole de test, gravités, limites, liste des 52 critères |
| `donnees-fictives-ruxaam-v1.22.json` | audit fictif à importer (bouton « Importer ») pour essayer l'outil |
| `LICENSE` | EUPL-1.2 |
| `README.md` | ce fichier |

## Licence et attributions
- **Code, textes d'impact et de test, thèmes, gravités et bonnes pratiques de RUXAAM** : © 2026 Bertrand Kempf, [EUPL-1.2](LICENSE).
- **Critères du RAAM 1.1** (intitulés, niveaux, références WCAG et EN 301 549) : © Service information et presse (SIP), Luxembourg, [CC BY 3.0 LU](https://creativecommons.org/licenses/by/3.0/lu/), reproduits sans modification. Le RAAM est lui-même dérivé de documents de la DINUM (RGAA). Source : <https://github.com/accessibility-luxembourg/ReferentielAccessibiliteMobile>. Ces éléments restent sous leur licence d'origine ; l'EUPL ne s'y applique pas.
  Modifications de RUXAAM : sélection de 52 critères, regroupement par thèmes, étapes de test, gravités, textes d'impact et de test.
- **jsPDF 2.5.1** (embarqué dans `ruxaam.html`) : © 2010-2021 James Hall et contributeurs, licence MIT. Les en-têtes de copyright de la bibliothèque et de ses greffons sont conservés dans le fichier.
- **WCAG 2.1** : © W3C. Les numéros et intitulés des critères de succès viennent du RAAM ; les textes de RUXAAM sont originaux.
- **Heuristiques d'utilisabilité** : Nielsen Norman Group, <https://www.nngroup.com/articles/ten-usability-heuristics/> (questions reformulées par RUXAAM, texte d'origine non reproduit).
- **Échelle de gravité** : noms des quatre niveaux inspirés de l'échelle d'impact de Deque (axe-core, MPL-2.0), aucun code repris.

RUXAAM n'est ni approuvé ni certifié par le SIP, l'OSAPS, le W3C ou Deque Systems.

## Contribuer
Ouvrez une issue avant une évolution importante. Les critères officiels (numéro, intitulé, niveau) ne se modifient pas. L'outil doit rester accessible (clavier, contrastes, lecteurs d'écran) et sans dépendance réseau. N'ajoutez aucune donnée confidentielle.
