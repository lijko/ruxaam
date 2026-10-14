# Documentation RUXAAM

## 1. Principe
RUXAAM sert à **trier avant d'auditer**. Il ne remplace pas l'audit complet du RAAM (108 critères) : il en retient 59 qui suffisent à repérer vite les barrières les plus fréquentes et les plus lourdes sur mobile, puis il aide à rédiger et prioriser les tickets.

## 2. Types d'audit
- **Audit rapide** : les 59 critères sur un échantillon d'écrans.
- **Fonctionnalité primaire** : fermer, retour, étapes, menu, navigation, formulaire, notification.
- **Scénario** : parcours complexe, critères + lecture UX.

Chaque onglet garde son propre taux, jamais fusionné avec un autre.

## 3. Statuts et taux
Quatre statuts par critère et par écran : **C** (conforme), **NC** (non conforme), **NT** (non testé), **NA** (non applicable). Le taux est calculé sans les NA. La couche POUR et heuristiques UX est qualitative et n'entre pas dans le taux, de même que les bonnes pratiques hors RAAM.

## 4. Sélection des critères
- 59 critères du RAAM 1.1 sur 108, intitulés, niveaux (A, AA) et références WCAG / EN 301 549 **identiques** au référentiel officiel.
- Sélection : les critères d’un contrôle rapide sur mobile, avec le lecteur d’écran de la plateforme, sans outil spécialisé (voir la liste en section 11).
- Les autres critères du RAAM restent à vérifier dans l'audit complet.

## 5. Règle « si présent »
24 critères sur 59 ne s'appliquent que si l'écran contient l'élément concerné. Six déclencheurs fermés, une question par déclencheur et par écran en tête de chaque onglet :

| Déclencheur | Question posée |
|---|---|
| CAPTCHA | Cet écran contient-il un CAPTCHA ? |
| Image complexe | Cet écran contient-il une image complexe (graphique, schéma, carte) ? |
| Média temporel ou son | Cet écran contient-il un média temporel (audio, vidéo) ou un son qui se lance seul ? |
| Tableau de données | Cet écran contient-il un tableau de données ? |
| Lien coloré dans un texte | Cet écran contient-il, dans un texte, un lien repérable seulement par sa couleur ? |
| Formulaire | Cet écran contient-il au moins un champ de saisie ? |

Répondre « Non » passe les critères liés en NA pour cet écran (y compris ceux déjà évalués, avec un message). « Oui » après un « Non » les remet en NT. Les critères restent visibles, avec la pastille « Si présent ».

## 6. Thèmes RUXAAM
Taxonomie propre à RUXAAM, qui regroupe les critères RAAM autrement que les 15 thèmes officiels, pour s'aligner sur la façon de travailler d'une équipe produit. Règle : tout ce qui empêche d'atteindre un élément ou un contenu au clavier relève de « Navigation & Structure ».

Navigation & Structure · Composants Interactifs · Images & Médias · Couleurs & Contrastes · Contenu & Lisibilité · Fondations Techniques · Formulaires.

## 7. Gravité
**La gravité n'est pas normative.** Ni le RAAM ni WCAG 2.x n'en définissent : un critère est conforme ou non. Les niveaux A et AA indiquent l'exigibilité, pas la gêne réelle.

La gravité de RUXAAM sert à **trier** les non-conformités et à **fixer la priorité** des tickets. C'est une valeur par défaut par critère, pensée pour un défaut qui touche un élément important de l'écran. L'impact réel dépend de l'écran : un bouton sans nom bloque sur « Payer », gêne sur un bouton de partage secondaire. Elle n'entre jamais dans le taux. Les gravités par défaut sont une **base de discussion**, non relue critère par critère avec les partenaires.

| Niveau | Repère | Priorité Jira |
|---|---|---|
| **Critique** | Empêche, pour au moins un groupe d'utilisateurs, d'accéder à une fonction ou à un contenu essentiel, sans contournement ; ou met la personne en danger (effets de flash). | Highest |
| **Sérieux** | Barrière forte : rend la tâche très difficile, et peut la bloquer selon le contexte. | High |
| **Modéré** | Difficulté réelle, mais un contournement existe et l'essentiel reste accessible. | Medium |
| **Mineur** | Gêne ou ralentissement, sans empêcher la tâche. | Low |

Pour choisir : la tâche reste-t-elle possible ? Pour qui (lecteur d'écran, clavier ou contacteur, basse vision, surdité, troubles cognitifs, motricité) ? Existe-t-il un contournement raisonnable ?

Répartition par défaut : 29 critères Sérieux, 13 Modéré, 12 Critique, 5 Mineur.

## 8. Bonnes pratiques hors RAAM
Trois bonnes pratiques, signalées « Hors RAAM » et exclues du taux :
- **bp1 — Zone tactile** : au moins 44×44 pt sur iOS, 48×48 dp sur Android (recommandations d'Apple et d'Android ; WCAG 2.2 demande 24 px au niveau AA, 44 px au niveau AAA).
- **bp2 — Retour ou fermeture** : chaque écran et chaque vue modale offre un moyen évident de revenir en arrière ou de se fermer.
- **bp3 — Retour du focus** : à la fermeture d'une fenêtre modale, le focus revient sur l'élément qui l'avait ouverte.

## 9. Limites
- Pré-diagnostic : ne produit ni déclaration d'accessibilité ni taux de conformité officiel.
- Pas de comparaison avec l'audit simplifié du SIP, fondé sur le RAWEB.
- Test réel sur VoiceOver et TalkBack à compléter.
- Les consignes de test sont des aides de lecture : la méthodologie officielle du RAAM fait foi.

## 10. Modifier l'outil
Tout est dans `ruxaam.html` : les critères et leurs textes se trouvent dans le bloc délimité par `DEBUT_DONNEES` et `FIN_DONNEES`. Ne modifiez jamais le numéro, l'intitulé ni le niveau d'un critère officiel.

## 11. Les 59 critères
Intitulés, niveaux et références du RAAM 1.1 © SIP Luxembourg, CC BY 3.0 LU. Thèmes (regroupement) et gravités : RUXAAM.

### Navigation & Structure (8)

| RAAM | Niveau | Gravité | Si présent | Intitulé |
|---|---|---|---|---|
| 5.2 | A | Critique |  | Chaque composant d’interface est-il contrôlable par le clavier et tout dispositif de pointage (hors cas particuliers) ? |
| 5.3 | A | Sérieux |  | Chaque changement de contexte respecte-t-il une de ces conditions ? |
| 7.1 | A | Modéré |  | Dans chaque écran, l’information est-elle structurée par l’utilisation appropriée de titres ? |
| 7.2 | A | Mineur |  | Dans chaque écran, chaque liste est-elle correctement structurée ? |
| 8.5 | A | Sérieux |  | Dans chaque écran, pour chaque élément recevant le focus, la prise de focus est-elle visible ? |
| 10.1 | A | Modéré |  | Dans chaque écran, l’ordre de tabulation au clavier est-il cohérent ? |
| 10.2 | A | Sérieux |  | Dans chaque écran, l’ordre de restitution par les technologies d’assistance est-il cohérent ? |
| 10.3 | A | Critique |  | Dans chaque écran, la navigation ne doit pas contenir de piège au clavier. Cette règle est-elle respectée ? |

### Composants Interactifs (11)

| RAAM | Niveau | Gravité | Si présent | Intitulé |
|---|---|---|---|---|
| 5.1 | A | Critique |  | Chaque composant d’interface est-il, si nécessaire, compatible avec les technologies d’assistance (hors cas particuliers) ? |
| 5.4 | AA | Sérieux |  | Dans chaque écran, les messages de statut sont-ils correctement restitués par les technologies d’assistance ? |
| 5.5 | A | Sérieux |  | Chaque état d’un contrôle à bascule présenté à l’utilisateur est-il perceptible ? |
| 8.7 | AA | Modéré |  | Dans chaque écran, les contenus additionnels apparaissant à la prise de focus ou au survol d’un composant d’interface sont-ils contrôlables par l’utilisateur (hors cas particuliers) ? |
| 11.1 | A | Sérieux |  | Pour chaque écran, l’utilisateur a-t-il le contrôle de chaque limite de temps modifiant le contenu (hors cas particuliers) ? |
| 11.2 | A | Sérieux |  | Pour chaque écran, chaque procédé limitant le temps d’une session peut-il être arrêté ou supprimé (hors cas particuliers) ? |
| 11.10 | A | Critique |  | Dans chaque écran, les fonctionnalités activables au moyen d’un geste complexe sont-elles activables au moyen d’un geste simple (hors cas particuliers) ? |
| 11.11 | A | Critique |  | Dans chaque écran, les fonctionnalités activables par la réalisation d’actions simultanées sont-elles activables au moyen d’une action unique. Cette règle est-elle respectée (hors cas particuliers) ? |
| 11.12 | A | Modéré |  | Dans chaque écran, les actions déclenchées au moyen d’un dispositif de pointage sur un point unique de l’écran peuvent-elles faire l’objet d’une annulation (hors cas particuliers) ? |
| 11.13 | A | Sérieux |  | Dans chaque écran, les fonctionnalités qui impliquent un mouvement de l’appareil ou vers l’appareil peuvent-elles être satisfaites de manière alternative (hors cas particuliers) ? |
| 11.15 | A | Critique |  | Chaque fonctionnalité d’identification ou de contrôle qui repose sur l’utilisation de caractéristiques biologiques de l’utilisateur dispose-t-elle d’une méthode alternative ? |

### Images & Médias (12)

| RAAM | Niveau | Gravité | Si présent | Intitulé |
|---|---|---|---|---|
| 1.1 | A | Mineur |  | Chaque élément graphique de décoration est-il ignoré par les technologies d’assistance ? |
| 1.2 | A | Critique |  | Chaque élément graphique porteur d’information possède-t-il une alternative accessible aux technologies d’assistance ? |
| 1.3 | A | Sérieux |  | Pour chaque élément graphique porteur d’information, l’alternative accessible aux technologies d’assistance est-elle pertinente (hors cas particuliers) ? |
| 1.4 | A | Sérieux | CAPTCHA | Pour chaque élément graphique utilisé comme CAPTCHA ou comme élément graphique de test, l’alternative restituée par les technologies d’assistance permet-elle d’identifier la nature et la fonction de l’élément graphique ? |
| 1.5 | A | Critique | CAPTCHA | Chaque élément graphique utilisé comme CAPTCHA possède-t-il une alternative ? |
| 1.6 | A | Modéré | Image complexe | Chaque élément graphique porteur d’information a-t-il, si nécessaire, une description détaillée ? |
| 1.8 | AA | Modéré |  | Chaque élément graphique texte porteur d’information, en l’absence d’un mécanisme de remplacement, doit, si possible être remplacé par du texte stylé. Cette règle est-elle respectée (hors cas particuliers) ? |
| 3.5 | A | Sérieux | Média temporel ou son | Chaque média temporel synchronisé pré-enregistré a-t-il, si nécessaire, une alternative (hors cas particuliers) ? |
| 3.7 | A | Critique | Média temporel ou son | Chaque média temporel synchronisé a-t-il, si nécessaire, des sous-titres synchronisés (hors cas particuliers) ? |
| 3.9 | AA | Sérieux | Média temporel ou son | Chaque média temporel pré-enregistré (seulement vidéo ou synchronisé) a-t-il, si nécessaire, une audiodescription synchronisée (hors cas particuliers) ? |
| 3.12 | A | Sérieux | Média temporel ou son | Chaque séquence sonore déclenchée automatiquement est-elle contrôlable par l’utilisateur ? |
| 3.13 | A | Sérieux | Média temporel ou son | Chaque média temporel a-t-il, si nécessaire, les fonctionnalités de contrôle de sa consultation ? |

### Couleurs & Contrastes (4)

| RAAM | Niveau | Gravité | Si présent | Intitulé |
|---|---|---|---|---|
| 2.1 | A | Sérieux |  | Dans chaque écran, l’information ne doit pas être donnée uniquement par la couleur. Cette règle est-elle respectée ? |
| 2.2 | AA | Sérieux |  | Dans chaque écran, le contraste entre la couleur du texte et la couleur de son arrière-plan est-il suffisamment élevé (hors cas particuliers) ? |
| 2.3 | AA | Sérieux |  | Dans chaque écran, les couleurs utilisées dans les composants d’interface et les éléments graphiques porteurs d’informations sont-elles suffisamment contrastées (hors cas particuliers) ? |
| 8.6 | A | Modéré |  | Dans chaque écran, l’information ne doit pas être donnée uniquement par la forme, taille ou position. Cette règle est-elle respectée ? |

### Contenu & Lisibilité (9)

| RAAM | Niveau | Gravité | Si présent | Intitulé |
|---|---|---|---|---|
| 4.3 | A | Mineur | Tableau de données | Chaque tableau de données a-t-il un titre ? |
| 4.5 | A | Sérieux | Tableau de données | Pour chaque tableau de données, les entêtes de lignes et de colonnes sont-ils correctement reliés aux cellules de données ? |
| 8.1 | A | Sérieux |  | Dans chaque écran, le contenu visible porteur d’information est-il accessible aux technologies d’assistance ? |
| 8.2 | AA | Sérieux |  | Dans chaque écran, l’utilisateur peut-il augmenter la taille des caractères de 200% au moins (hors cas particuliers) ? |
| 8.3 | A | Modéré | Lien coloré dans un texte | Dans chaque écran, chaque composant en environnement de texte dont la nature n’est pas évidente a-t-il un rapport de contraste supérieur ou égal à 3:1 par rapport au texte environnant ? |
| 8.4 | A | Modéré | Lien coloré dans un texte | Dans chaque écran, pour chaque composant en environnement de texte dont la nature n’est pas évidente, une indication autre que la couleur permet-elle de signaler la prise de focus et le survol à la souris ? |
| 11.7 | A | Critique |  | Dans chaque écran, les changements brusques de luminosité ou les effets de flash sont-ils correctement utilisés ? |
| 11.8 | A | Sérieux |  | Dans chaque écran, chaque contenu en mouvement ou clignotant est-il contrôlable par l’utilisateur ? |
| 11.9 | AA | Sérieux |  | Dans chaque écran, le contenu proposé est-il consultable quelle que soit l’orientation de l’écran (portrait ou paysage) (hors cas particuliers) ? |

### Fondations Techniques (3)

| RAAM | Niveau | Gravité | Si présent | Intitulé |
|---|---|---|---|---|
| 6.1 | A | Sérieux |  | Dans chaque écran, les textes sont-ils restitués par les technologies d’assistance dans la langue principale de l’écran ? |
| 6.2 | A | Modéré |  | Dans chaque écran, les éléments de l’interface ne doivent pas être utilisés uniquement à des fins de présentation. Cette règle est-elle respectée ? |
| 12.3 | A | Critique |  | L’application ne perturbe pas les fonctionnalités d’accessibilité de la plateforme. Cette règle est-elle respectée ? |

### Formulaires (12)

| RAAM | Niveau | Gravité | Si présent | Intitulé |
|---|---|---|---|---|
| 9.1 | A | Sérieux | Formulaire | Chaque champ de formulaire a-t-il une étiquette visible ? |
| 9.2 | A | Critique | Formulaire | Chaque champ de formulaire a-t-il une étiquette accessible aux technologies d’assistance ? |
| 9.3 | A | Sérieux | Formulaire | Chaque étiquette associée à un champ de formulaire est-elle pertinente ? |
| 9.4 | A | Mineur | Formulaire | Chaque étiquette de champ et son champ associé sont-ils accolés ? |
| 9.5 | A | Sérieux | Formulaire | Dans chaque formulaire, l’intitulé de chaque bouton est-il pertinent ? |
| 9.6 | A | Sérieux | Formulaire | Dans chaque formulaire, les champs de même nature sont-ils identifiés, si nécessaire ? |
| 9.7 | A | Modéré | Formulaire | Les champs de formulaire obligatoires sont-ils correctement identifiés (hors cas particuliers) ? |
| 9.8 | A | Modéré | Formulaire | Pour chaque champ de formulaire qui attend un type de données et/ou un format spécifique, l’information correspondante est-elle disponible ? |
| 9.9 | A | Sérieux | Formulaire | Dans chaque formulaire, les erreurs de saisie sont-elles accessibles ? |
| 9.10 | AA | Modéré | Formulaire | Dans chaque formulaire, le contrôle de saisie est-il accompagné, si nécessaire, de suggestions des types, formats de données ou valeurs attendus ? |
| 9.11 | AA | Sérieux | Formulaire | Pour chaque formulaire qui modifie ou supprime des données, ou qui transmet des réponses à un test ou à un examen, ou dont la validation a des conséquences financières ou juridiques, les données saisies peuvent-elles être modifiées, mises à jour ou récupérées par l’utilisateur ? |
| 9.12 | AA | Mineur | Formulaire | Pour chaque champ qui attend une donnée personnelle de l’utilisateur, la saisie est-elle facilitée ? |