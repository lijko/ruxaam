# Documentation RUXAAM

## 1. Principe
RUXAAM sert à **trier avant d'auditer**. Il ne remplace pas l'audit complet du RAAM (108 critères) : il en retient 52 qui suffisent à repérer vite les barrières les plus fréquentes et les plus lourdes sur mobile, puis il aide à rédiger et prioriser les tickets.

## 2. Types d'audit
- **Audit rapide** : les 52 critères sur un échantillon d'écrans.
- **Fonctionnalité primaire** : fermer, retour, étapes, menu, navigation, formulaire, notification.
- **Scénario** : parcours complexe, critères + lecture UX.

Chaque onglet garde son propre taux, jamais fusionné avec un autre.

## 3. Statuts et taux
Quatre statuts par critère et par écran : **C** (conforme), **NC** (non conforme), **NT** (non testé), **NA** (non applicable). Le taux est calculé sans les NA. La couche POUR et heuristiques UX est qualitative et n'entre pas dans le taux, de même que les bonnes pratiques hors RAAM.

## 4. Sélection des critères
- 52 critères du RAAM 1.1 sur 108, intitulés, niveaux (A, AA) et références WCAG / EN 301 549 **identiques** au référentiel officiel.
- Sélection : les critères d’un contrôle rapide sur mobile, avec le lecteur d’écran de la plateforme, sans outil spécialisé (voir la liste en section 12).
- Plus 3 bonnes pratiques hors RAAM (section 9), soit 57 éléments dans l'outil.

## 5. Règle « si présent »
20 critères sur 52 ne s'appliquent que si l'écran (ou l'application) contient l'élément concerné. Chacun est rattaché à l'un des six déclencheurs ci-dessous, indiqué par la pastille « Si présent · <déclencheur> ».

En tête de chaque onglet RAAM, le panneau **« Contenu des écrans »** porte un interrupteur par écran et par élément, plus un interrupteur « Limite de session » valable pour toute l'application. Tout est désactivé au départ. Un critère « si présent » ne s'affiche que si au moins un écran contient l'élément ; sur un écran qui ne le contient pas, il affiche « Absent » et compte comme NA. Rien n'est effacé : réactiver un interrupteur retrouve les statuts et commentaires. Une ligne sous le tableau indique combien de critères restent masqués. Une sauvegarde plus ancienne garde visibles les critères « si présent » déjà évalués, pour que le taux ne change pas.

| Déclencheur | Le critère s'applique si… | Critères |
|---|---|---|
| CAPTCHA | l'écran contient un CAPTCHA | 1.4, 1.5 |
| Image complexe | l'écran contient une image complexe (graphique, schéma, carte) | 1.6 |
| Média temporel ou son | l'écran contient un média temporel (audio, vidéo) ou un son qui se lance seul | 3.5, 3.7, 3.9, 3.12, 3.13 |
| Tableau de données | l'écran contient un tableau de données | 4.5 |
| Formulaire | l'écran contient au moins un champ de saisie | 9.1, 9.2, 9.3, 9.5, 9.6, 9.7, 9.8, 9.9, 9.10, 9.11 |
| Limite de session | l'application limite la durée d'une session (déconnexion automatique, expiration) | 11.2 |

## 6. Protocole de test en 4 étapes
Un audit rapide se fait en 4 étapes, toujours dans cet ordre, sur les mêmes écrans. Chaque critère est rattaché à l'étape où on le constate le plus facilement (pastille « Étape … ») ; on peut répondre au fil des étapes.

1. **Usage standard** — aucun réglage d'accessibilité activé : contenus, images, couleurs et contrastes, composants, formulaires, messages.
2. **Agrandissement** — deux passes, en remettant le réglage par défaut entre les deux : texte agrandi (iOS : Affichage et taille du texte ; Android : Taille de la police), puis affichage agrandi (iOS : Zoom de l'affichage ; Android : Taille de l'affichage). Critère 8.2 et bonne pratique zone tactile.
3. **Lecteur d'écran** — VoiceOver (iOS) ou TalkBack (Android), en balayant d'élément en élément. 3a : contenus et structure ; 3b : composants, formulaires et annonces. C'est l'étape qui concentre le plus de critères.
4. **Navigation alternative** — clavier externe (Bluetooth), commande vocale ; contrôle de sélection (iOS) et Switch Access (Android) optionnels en audit rapide.

Un critère se constate parfois à plusieurs étapes : l'outil indique l'étape principale, mais un doute à une autre étape compte. En cas de résultats différents, retiens le pire (NC l'emporte sur C). Le test sur appareil réel est la référence : les simulateurs ne reproduisent pas fidèlement VoiceOver et TalkBack.

Séquence construite par RUXAAM à partir des pratiques décrites par Apple et Android ; ce n'est pas un protocole officiel.

Répartition (étape principale) : 1. Usage standard : 23 éléments ; 2. Agrandissement : 1 ; 3. Lecteur d'écran : 24 ; 4. Navigation alternative : 7.

**Vue « Par étape de test »** : dans un onglet RAAM, le commutateur « Vue : Par thème | Par étape de test » range la liste selon ces étapes, avec un rappel de la consigne en tête de chaque étape. Un critère n'apparaît qu'une fois. Statuts, taux et exports ne changent pas.

**Plateforme** : sous le nom de l'audit, choisis iOS, Android ou Multiplateforme (un second clic désélectionne). Convention : un audit = une plateforme. Dans l'export Jira, la rubrique « Per platform » ne contient que la plateforme choisie (iOS et Android si aucune), et chaque ticket reçoit l'étiquette `ios`, `android` ou `multiplateforme`.

**Élément concerné** : sous chaque critère non conforme, pour chaque écran concerné, un champ d'une ligne désigne l'élément en cause avec une notation simple, détaillée dans l'Aide (« Noter les éléments ») :

| Ce que tu désignes | Notation | Exemple |
|---|---|---|
| Un écran | `Écran` | `Produits` |
| Un élément | `Écran[type]` | `Produits[list]` |
| Un élément avec son libellé | `Écran[type "Libellé"]` | `Accueil[button "Connexion"]` |
| Un élément avec un état | `Écran[type "Libellé"] (état)` | `Accueil[button "Valider"] (disabled)` |
| Un parcours | `Écran -> Écran` | `Accueil -> Produits -> Détail produit` |

L'export Jira reprend l'élément dans le titre et dans « Flow(s) / Screen(s) / Element(s) in concern ».

**Mémoire des exports Jira** : l'outil retient, pour tout l'audit, les critères déjà exportés (la mémoire fait partie de la sauvegarde) et ne les exporte pas deux fois : « 3 ticket(s) déjà exporté(s), 2 nouveau(x) ». « Tickets Jira — tout réexporter » reprend tous les critères non conformes, par exemple si l'import dans Jira a échoué. Le champ « Ticket Jira » des versions précédentes n'existe plus.

**Exports** : aucun fichier vide n'est produit. Sans onglet, sans onglet RAAM, sans critère testé ou sans critère non conforme, un message explique pourquoi l'export n'a pas lieu. À l'import d'une sauvegarde plus ancienne, l'outil indique combien de critères de la sauvegarde n'existent plus dans cette version, et combien étaient non conformes.

## 7. Thèmes RUXAAM
Taxonomie propre à RUXAAM, qui regroupe les critères RAAM autrement que les 15 thèmes officiels, pour s'aligner sur la façon de travailler d'une équipe produit. Règle : tout ce qui empêche d'atteindre un élément ou un contenu au clavier relève de « Navigation & Structure ».

Navigation & Structure · Composants Interactifs · Images & Médias · Couleurs & Contrastes · Contenu & Lisibilité · Fondations Techniques · Formulaires.

## 8. Gravité
**La gravité n'est pas normative.** Ni le RAAM ni WCAG 2.x n'en définissent : un critère est conforme ou non. Les niveaux A et AA indiquent l'exigibilité, pas la gêne réelle.

La gravité de RUXAAM sert à **trier** les non-conformités et à **fixer la priorité** des tickets. C'est une valeur par défaut par critère, pensée pour un défaut qui touche un élément important de l'écran. L'impact réel dépend de l'écran : un bouton sans nom bloque sur « Payer », gêne sur un bouton de partage secondaire. Elle n'entre jamais dans le taux. Les gravités par défaut sont une **base de discussion**, non relue critère par critère avec les partenaires.

| Niveau | Repère | Priorité Jira |
|---|---|---|
| **Critique** | Empêche, pour au moins un groupe d'utilisateurs, d'accéder à une fonction ou à un contenu essentiel, sans contournement ; ou met la personne en danger (effets de flash). | Highest |
| **Sérieux** | Barrière forte : rend la tâche très difficile, et peut la bloquer selon le contexte. | High |
| **Modéré** | Difficulté réelle, mais un contournement existe et l'essentiel reste accessible. | Medium |
| **Mineur** | Gêne ou ralentissement, sans empêcher la tâche. | Low |

Pour choisir : la tâche reste-t-elle possible ? Pour qui (lecteur d'écran, clavier ou contacteur, basse vision, surdité, troubles cognitifs, motricité) ? Existe-t-il un contournement raisonnable ?

Répartition par défaut des 52 critères RAAM : 29 Sérieux, 12 Critique, 10 Modéré, 1 Mineur.

## 9. Bonnes pratiques hors RAAM
Trois bonnes pratiques, signalées « Hors RAAM » et exclues du taux :
- **bp1 — Zone tactile** : au moins 44×44 pt sur iOS, 48×48 dp sur Android (recommandations d'Apple et d'Android ; WCAG 2.2 demande 24 px au niveau AA, 44 px au niveau AAA).
- **bp2 — Retour ou fermeture** : chaque écran et chaque vue modale offre un moyen évident de revenir en arrière ou de se fermer.
- **bp3 — Retour du focus** : à la fermeture d'une fenêtre modale, le focus revient sur l'élément qui l'avait ouverte.

## 10. Limites
- Pré-diagnostic : ne produit ni déclaration d'accessibilité ni taux de conformité officiel.
- Pas de comparaison avec l'audit simplifié du SIP, fondé sur le RAWEB.
- Test réel sur VoiceOver et TalkBack à compléter.
- Un critère déjà exporté vers Jira qui devient non conforme sur un autre écran n'est pas réexporté automatiquement : utilise « Tickets Jira — tout réexporter » ou complète le ticket existant.
- Les consignes de test sont des aides de lecture : la méthodologie officielle du RAAM fait foi.

## 11. Modifier l'outil
Tout est dans `ruxaam.html` : les critères et leurs textes se trouvent dans le bloc délimité par `DEBUT_DONNEES` et `FIN_DONNEES`, généré depuis le dépôt de développement (<https://github.com/lijko/ruxal-a11y>). Ne modifiez jamais le numéro, l'intitulé ni le niveau d'un critère officiel.

## 12. Les 52 critères
Intitulés, niveaux et références du RAAM 1.1 © SIP Luxembourg, CC BY 3.0 LU. Thèmes (regroupement), gravités et étapes : RUXAAM.

### Navigation & Structure (7)

| RAAM | Niveau | Gravité | Étape | Si présent | Intitulé |
|---|---|---|---|---|---|
| 5.2 | A | Critique | 4 |  | Chaque composant d’interface est-il contrôlable par le clavier et tout dispositif de pointage (hors cas particuliers) ? |
| 5.3 | A | Sérieux | 4 |  | Chaque changement de contexte respecte-t-il une de ces conditions ? |
| 7.1 | A | Modéré | 3a |  | Dans chaque écran, l’information est-elle structurée par l’utilisation appropriée de titres ? |
| 8.5 | A | Sérieux | 4 |  | Dans chaque écran, pour chaque élément recevant le focus, la prise de focus est-elle visible ? |
| 10.1 | A | Modéré | 4 |  | Dans chaque écran, l’ordre de tabulation au clavier est-il cohérent ? |
| 10.2 | A | Sérieux | 3a |  | Dans chaque écran, l’ordre de restitution par les technologies d’assistance est-il cohérent ? |
| 10.3 | A | Critique | 4 |  | Dans chaque écran, la navigation ne doit pas contenir de piège au clavier. Cette règle est-elle respectée ? |

### Composants Interactifs (11)

| RAAM | Niveau | Gravité | Étape | Si présent | Intitulé |
|---|---|---|---|---|---|
| 5.1 | A | Critique | 3b |  | Chaque composant d’interface est-il, si nécessaire, compatible avec les technologies d’assistance (hors cas particuliers) ? |
| 5.4 | AA | Sérieux | 3b |  | Dans chaque écran, les messages de statut sont-ils correctement restitués par les technologies d’assistance ? |
| 5.5 | A | Sérieux | 3b |  | Chaque état d’un contrôle à bascule présenté à l’utilisateur est-il perceptible ? |
| 8.7 | AA | Modéré | 4 |  | Dans chaque écran, les contenus additionnels apparaissant à la prise de focus ou au survol d’un composant d’interface sont-ils contrôlables par l’utilisateur (hors cas particuliers) ? |
| 11.1 | A | Sérieux | 1 |  | Pour chaque écran, l’utilisateur a-t-il le contrôle de chaque limite de temps modifiant le contenu (hors cas particuliers) ? |
| 11.2 | A | Sérieux | 1 | Limite de session | Pour chaque écran, chaque procédé limitant le temps d’une session peut-il être arrêté ou supprimé (hors cas particuliers) ? |
| 11.10 | A | Critique | 3b |  | Dans chaque écran, les fonctionnalités activables au moyen d’un geste complexe sont-elles activables au moyen d’un geste simple (hors cas particuliers) ? |
| 11.11 | A | Critique | 3b |  | Dans chaque écran, les fonctionnalités activables par la réalisation d’actions simultanées sont-elles activables au moyen d’une action unique. Cette règle est-elle respectée (hors cas particuliers) ? |
| 11.12 | A | Modéré | 1 |  | Dans chaque écran, les actions déclenchées au moyen d’un dispositif de pointage sur un point unique de l’écran peuvent-elles faire l’objet d’une annulation (hors cas particuliers) ? |
| 11.13 | A | Sérieux | 1 |  | Dans chaque écran, les fonctionnalités qui impliquent un mouvement de l’appareil ou vers l’appareil peuvent-elles être satisfaites de manière alternative (hors cas particuliers) ? |
| 11.15 | A | Critique | 1 |  | Chaque fonctionnalité d’identification ou de contrôle qui repose sur l’utilisation de caractéristiques biologiques de l’utilisateur dispose-t-elle d’une méthode alternative ? |

### Images & Médias (11)

| RAAM | Niveau | Gravité | Étape | Si présent | Intitulé |
|---|---|---|---|---|---|
| 1.1 | A | Mineur | 3a |  | Chaque élément graphique de décoration est-il ignoré par les technologies d’assistance ? |
| 1.2 | A | Critique | 3a |  | Chaque élément graphique porteur d’information possède-t-il une alternative accessible aux technologies d’assistance ? |
| 1.3 | A | Sérieux | 3a |  | Pour chaque élément graphique porteur d’information, l’alternative accessible aux technologies d’assistance est-elle pertinente (hors cas particuliers) ? |
| 1.4 | A | Sérieux | 3a | CAPTCHA | Pour chaque élément graphique utilisé comme CAPTCHA ou comme élément graphique de test, l’alternative restituée par les technologies d’assistance permet-elle d’identifier la nature et la fonction de l’élément graphique ? |
| 1.5 | A | Critique | 1 | CAPTCHA | Chaque élément graphique utilisé comme CAPTCHA possède-t-il une alternative ? |
| 1.6 | A | Modéré | 3a | Image complexe | Chaque élément graphique porteur d’information a-t-il, si nécessaire, une description détaillée ? |
| 3.5 | A | Sérieux | 1 | Média temporel ou son | Chaque média temporel synchronisé pré-enregistré a-t-il, si nécessaire, une alternative (hors cas particuliers) ? |
| 3.7 | A | Critique | 1 | Média temporel ou son | Chaque média temporel synchronisé a-t-il, si nécessaire, des sous-titres synchronisés (hors cas particuliers) ? |
| 3.9 | AA | Sérieux | 1 | Média temporel ou son | Chaque média temporel pré-enregistré (seulement vidéo ou synchronisé) a-t-il, si nécessaire, une audiodescription synchronisée (hors cas particuliers) ? |
| 3.12 | A | Sérieux | 1 | Média temporel ou son | Chaque séquence sonore déclenchée automatiquement est-elle contrôlable par l’utilisateur ? |
| 3.13 | A | Sérieux | 1 | Média temporel ou son | Chaque média temporel a-t-il, si nécessaire, les fonctionnalités de contrôle de sa consultation ? |

### Couleurs & Contrastes (4)

| RAAM | Niveau | Gravité | Étape | Si présent | Intitulé |
|---|---|---|---|---|---|
| 2.1 | A | Sérieux | 1 |  | Dans chaque écran, l’information ne doit pas être donnée uniquement par la couleur. Cette règle est-elle respectée ? |
| 2.2 | AA | Sérieux | 1 |  | Dans chaque écran, le contraste entre la couleur du texte et la couleur de son arrière-plan est-il suffisamment élevé (hors cas particuliers) ? |
| 2.3 | AA | Sérieux | 1 |  | Dans chaque écran, les couleurs utilisées dans les composants d’interface et les éléments graphiques porteurs d’informations sont-elles suffisamment contrastées (hors cas particuliers) ? |
| 8.6 | A | Modéré | 1 |  | Dans chaque écran, l’information ne doit pas être donnée uniquement par la forme, taille ou position. Cette règle est-elle respectée ? |

### Contenu & Lisibilité (6)

| RAAM | Niveau | Gravité | Étape | Si présent | Intitulé |
|---|---|---|---|---|---|
| 4.5 | A | Sérieux | 3a | Tableau de données | Pour chaque tableau de données, les entêtes de lignes et de colonnes sont-ils correctement reliés aux cellules de données ? |
| 8.1 | A | Sérieux | 3a |  | Dans chaque écran, le contenu visible porteur d’information est-il accessible aux technologies d’assistance ? |
| 8.2 | AA | Sérieux | 2 |  | Dans chaque écran, l’utilisateur peut-il augmenter la taille des caractères de 200% au moins (hors cas particuliers) ? |
| 11.7 | A | Critique | 1 |  | Dans chaque écran, les changements brusques de luminosité ou les effets de flash sont-ils correctement utilisés ? |
| 11.8 | A | Sérieux | 1 |  | Dans chaque écran, chaque contenu en mouvement ou clignotant est-il contrôlable par l’utilisateur ? |
| 11.9 | AA | Sérieux | 1 |  | Dans chaque écran, le contenu proposé est-il consultable quelle que soit l’orientation de l’écran (portrait ou paysage) (hors cas particuliers) ? |

### Fondations Techniques (3)

| RAAM | Niveau | Gravité | Étape | Si présent | Intitulé |
|---|---|---|---|---|---|
| 6.1 | A | Sérieux | 3a |  | Dans chaque écran, les textes sont-ils restitués par les technologies d’assistance dans la langue principale de l’écran ? |
| 6.2 | A | Modéré | 3a |  | Dans chaque écran, les éléments de l’interface ne doivent pas être utilisés uniquement à des fins de présentation. Cette règle est-elle respectée ? |
| 12.3 | A | Critique | 3b |  | L’application ne perturbe pas les fonctionnalités d’accessibilité de la plateforme. Cette règle est-elle respectée ? |

### Formulaires (10)

| RAAM | Niveau | Gravité | Étape | Si présent | Intitulé |
|---|---|---|---|---|---|
| 9.1 | A | Sérieux | 1 | Formulaire | Chaque champ de formulaire a-t-il une étiquette visible ? |
| 9.2 | A | Critique | 3b | Formulaire | Chaque champ de formulaire a-t-il une étiquette accessible aux technologies d’assistance ? |
| 9.3 | A | Sérieux | 3b | Formulaire | Chaque étiquette associée à un champ de formulaire est-elle pertinente ? |
| 9.5 | A | Sérieux | 3b | Formulaire | Dans chaque formulaire, l’intitulé de chaque bouton est-il pertinent ? |
| 9.6 | A | Sérieux | 3b | Formulaire | Dans chaque formulaire, les champs de même nature sont-ils identifiés, si nécessaire ? |
| 9.7 | A | Modéré | 3b | Formulaire | Les champs de formulaire obligatoires sont-ils correctement identifiés (hors cas particuliers) ? |
| 9.8 | A | Modéré | 3b | Formulaire | Pour chaque champ de formulaire qui attend un type de données et/ou un format spécifique, l’information correspondante est-elle disponible ? |
| 9.9 | A | Sérieux | 3b | Formulaire | Dans chaque formulaire, les erreurs de saisie sont-elles accessibles ? |
| 9.10 | AA | Modéré | 1 | Formulaire | Dans chaque formulaire, le contrôle de saisie est-il accompagné, si nécessaire, de suggestions des types, formats de données ou valeurs attendus ? |
| 9.11 | AA | Sérieux | 1 | Formulaire | Pour chaque formulaire qui modifie ou supprime des données, ou qui transmet des réponses à un test ou à un examen, ou dont la validation a des conséquences financières ou juridiques, les données saisies peuvent-elles être modifiées, mises à jour ou récupérées par l’utilisateur ? |
