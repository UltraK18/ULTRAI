# ULTRAI

Une application de bureau Windows pour un travail avec l'IA qui ne s'interrompt pas. Quatre modes dans une seule fenêtre — discuter, construire dans un vrai dossier de projet, concevoir sur un canevas, générer des images et des vidéos — plus la planification, les exécutions multi-agents, et votre téléphone comme second écran.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> Ce dépôt sert uniquement à la **distribution des versions**. Le code source n'est pas publié ici.

---

## Téléchargement

Windows 10 / 11 (x64). Nécessite le runtime WebView2, déjà présent sur la plupart des installations Windows.

**[Téléchargez la dernière version](https://github.com/UltraK18/ULTRAI/releases/latest)** — récupérez `ULTRAI_x.y.z_x64_en-US.msi` et exécutez-le.

Ensuite, l'application se gère elle-même : elle vérifie les nouvelles versions au lancement et périodiquement, vous prévient quand une mise à jour est disponible, et l'installe sur place.

## Quatre modes, une seule fenêtre

Chaque mode est un écran conçu spécifiquement, avec ses propres outils et ses propres agents — mais une seule application, un seul ensemble de réglages, un seul endroit où vit votre historique.

| Mode | L'écran | Ce que vous y faites |
| :--- | :--- | :--- |
| **Chat** | Conversation | N'importe quel fournisseur et modèle, effort de raisonnement par message, recherche approfondie avec citations, fichiers et images en entrée |
| **Code** | Un vrai dossier de projet | Arborescence de fichiers, diffs dans un panneau de revue, un terminal à côté du chat, demandes de permission avant que quoi que ce soit touche le disque |
| **Design** | Canevas en direct + agent designer | Les écrans s'affichent à côté du chat au fur et à mesure de leur construction ; le travail terminé est transmis à Code sous forme de fichiers réels |
| **Studio** | Canevas libre + chat | Générez des images et des vidéos, placez-les et réarrangez-les, déposez vos propres fichiers, continuez à itérer sur ce qui s'y trouve |

Changer de mode ne redémarre rien — chaque mode conserve ses propres conversations, et la barre latérale affiche celles qui appartiennent à l'endroit où vous êtes.

## L'interface est l'essentiel

La plupart des outils de ce domaine ne sont qu'un terminal ou une page web dans un wrapper. ULTRAI est une application de bureau qui a été conçue, et non assemblée.

- **Du verre qui est vraiment du verre** — les surfaces flottantes utilisent un petit moteur de rendu, pas un filtre de flou.
  Il calcule une normal map pour la bordure et en tire des reflets spéculaires, puis déplace ce qui se trouve derrière
  la surface pour que les bords réfractent. Des contrôles comme l'interrupteur et le curseur vont plus loin et résolvent
  la réfraction de Snell avec un indice de réfraction et une épaisseur, si bien que le curseur courbe la piste en dessous.
  Un flou CSS ne peut pas faire cela, et la différence se voit sur chaque bord.
- **Coins en squircle** — les panneaux utilisent une superellipse, pas un arc circulaire, si bien que la courbe rejoint
  le bord droit sans le méplat que produit `border-radius`.
- **Deux thèmes, tous deux réfléchis** — le clair et le sombre sont construits sur une seule palette aux tons béton
  avec une légère dominante froide, réglée pour que rien ne soit criard à aucune des deux extrémités. Chaque surface
  est un token, si bien que toute l'application évolue ensemble au lieu de dériver écran par écran.
- **Une sobriété voulue** — aucun emoji nulle part dans le produit, aucun point d'exclamation, aucun enthousiasme
  forcé. Chaque panneau porte une seule surface ; la séparation vient de la lumière de contour et de l'ombre plutôt
  que de boîtes dessinées dans des boîtes.
- **Une fenêtre sans coupure** — une barre de titre de 32 px aux dimensions Windows 11, qui partage l'arrière-plan
  de l'application, de sorte que le chrome ne se lit pas comme une bande séparée au-dessus du contenu.
- **Le mobile est une disposition différente, pas une version réduite** — feuilles inférieures (bottom sheets),
  contrôles pleine largeur et zones tactiles dimensionnées pour le doigt, décidées par l'appareil plutôt que par
  la largeur de la fenêtre.

## Génération, avec de vrais modèles

Studio n'est pas un point d'accès à un seul modèle d'image. Il choisit dans un catalogue pour chaque tâche et vous indique quel modèle il a utilisé et pourquoi.

- **Vidéo** — Veo 3.1 et Veo 3.0 (ainsi que leurs variantes rapides), Sora 2 et Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Image** — GPT Image 2 et 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (et Flash Lite), Grok Imagine Image
- **Vidéo en entrée, vidéo en sortie** — fournissez-lui un clip existant en entrée, pas seulement une invite
- **Il vérifie son propre travail** — extrait des images de ce qu'il a généré, les examine, et décide s'il faut recommencer
- **La durée, le format et la qualité sont les vôtres** — demandez 30 secondes, et ce sont 30 secondes qui seront produites, dans le format demandé

Les modèles auxquels vous avez accès dépendent des comptes fournisseurs que vous connectez (Vertex AI, OpenAI, xAI).

## Mode ULTRA — plusieurs agents, une seule tâche

Pour les travaux trop volumineux pour un seul contexte. ULTRA décompose la tâche en sous-tâches, les exécute à travers plusieurs agents phase par phase, et fait **vérifier les résultats de manière indépendante avant leur fusion** — un critique et des contrôles contradictoires, pas le même agent qui s'évalue lui-même. Vous observez l'exécution et pouvez intervenir à tout moment. Le modèle et l'effort de raisonnement sont définis par rôle, si bien qu'un worker économique et un vérificateur coûteux peuvent volontairement provenir de fournisseurs différents.

## Il tient ses rendez-vous

Dites « tous les jours de semaine à 9 h » ou « dans deux heures » et cela devient une tâche réelle, pas une simple note. Quand elle se déclenche, la tâche arrive comme un tour dans cette conversation et l'IA se met au travail.

- Un calendrier et une liste affichent tout ce qui est enregistré ; la prochaine exécution figure en bas de la barre latérale
- Fermé au moment où quelque chose devait se déclencher ? L'application détermine ce qu'elle a manqué et le regroupe en une seule exécution de rattrapage
- `/loop` répète une tâche pour autant de tours que vous le définissez

## Des objectifs que l'IA ne peut pas déclarer terminés

Définissez un objectif pour une conversation, et une évaluation indépendante conditionne son achèvement. L'agent qui effectue le travail n'a pas le pouvoir de décider qu'il a terminé.

## Une recherche qui creuse, et des questions avant de se mettre au travail

**La recherche approfondie** (deep research) planifie les angles d'approche, puis cherche et lit en parallèle à travers des sous-agents, et cite ce qu'elle a trouvé. La recherche du quotidien est elle aussi inhabituellement rigoureuse : le modèle a pour consigne de chercher plutôt que de deviner, d'utiliser la date du jour plutôt qu'une année héritée de son entraînement, et de vérifier les affirmations au présent avant de répondre. Les résultats sont présentés de manière équilibrée, avec les sources en ligne.

**L'entretien approfondi** (deep interview) — lorsqu'une demande est sous-spécifiée, transforme la conversation en un entretien structuré et détermine précisément ce que vous voulez réellement avant que le travail ne commence.

## Un travail qui s'exécute pendant que vous faites autre chose

Les tâches longues ne tiennent pas la fenêtre en otage.

- **Exécutions en arrière-plan** — confiez une tâche et elle s'exécute de façon isolée, comme une bifurcation (fork)
  de la conversation ou comme un sous-agent, et peut demander une permission supplémentaire en cours de route si
  elle se heurte à un obstacle.
- **Un moniteur en direct** — une barre en bas affiche tout ce qui est en cours à la fois : vos propres tâches en
  arrière-plan, celles lancées ailleurs, les appels de sous-agents en cours, les exécutions ULTRA, et toute commande
  shell qui tourne depuis un moment. Cliquez pour ouvrir celle que vous voulez suivre.
- **Bifurquer une conversation (fork)** — créez une branche à partir de n'importe quel point pour essayer quelque
  chose sans perdre l'original, et passez d'une branche à l'autre depuis l'index des messages.

## Transmission entre les modes

Le travail ne reste pas bloqué dans le mode où il a commencé. Design transmet les écrans terminés à Code sous forme de
fichiers réels sur le disque. Les sessions Code s'échangent questions et résultats entre elles. Studio place directement
sur le canevas ce qu'un agent a produit. Chaque transmission déplace de vrais fichiers ou de vrais tours de conversation,
pas un simple bloc de texte copié.

## Un espace de travail que l'IA peut utiliser sans toucher à vos fichiers

Le mode Chat dispose de son propre espace de travail temporaire sur le disque. L'IA peut y écrire, lire, exécuter et
réviser librement — brouillons, scripts, fichiers intermédiaires — sans vous demander une permission à chaque étape et
sans toucher à vos dossiers. Vous n'avez jamais à vous demander où cela se trouve ; vous obtenez simplement le résultat,
et vos propres répertoires restent intacts sauf si vous les désignez vous-même.

## Des sessions qui se parlent entre elles

En mode Code, une session peut transmettre une question ou un résultat à une autre — celle qui travaille sur le backend peut interroger celle qui connaît le frontend. Les messages arrivent comme un vrai tour dans l'autre conversation. C'est vous qui ouvrez le canal ; rien ne se connecte tout seul.

## Votre téléphone comme second écran

Activez le serveur et ouvrez ULTRAI depuis le navigateur de votre téléphone, sur le même réseau. La disposition mobile est conçue pour le tactile — feuilles inférieures et contrôles pleine largeur — et non pour une version réduite du bureau. Conversations, modèles et réglages sont partagés, si bien que vous reprenez exactement là où vous vous étiez arrêté.

## Faites-en votre outil

Tout ce qui suit est un simple fichier sur votre disque, que vous pouvez lire, modifier et versionner.

- **Agents** — `~/.ultrai/agents/*.md`. Le frontmatter décide de tout : dans quels modes l'agent apparaît, quels outils il peut utiliser, quelles sections de prompt il reçoit, quelles fonctionnalités (recherche, objectifs, entretien) lui sont autorisées. Modifiable depuis Réglages, et les agents intégrés peuvent être restaurés à leur état d'origine à tout moment.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Des instructions réutilisables que le modèle peut convoquer, ou que vous pouvez invoquer comme commande slash. Chacune peut être activée ou désactivée individuellement.
- **Modules de prompt** — le prompt système est assemblé à partir d'un catalogue, et le frontmatter de chaque agent choisit les sections qu'il reçoit. Sans rien déclarer, le prompt de l'agent est identique octet pour octet au défaut ; on peut opter pour des sections supplémentaires afin de changer sa façon de raisonner. Chaque mode dispose de son propre prompt, construit pour ce type de travail, plutôt qu'un prompt unique forcé de tout couvrir.
- **Serveurs MCP** — déclarés dans `ultrai.jsonc`. Locaux ou distants, avec authentification si nécessaire, activables ou désactivables serveur par serveur.
- **Mémoire** — conservée dans trois catégories (à propos de vous, sujets, domaines), les résumés sont injectés et les détails récupérés à la demande, avec un nettoyage périodique qui fusionne les doublons et les contradictions. Réservée au mode Chat, et vous pouvez consulter et supprimer chaque entrée depuis Réglages.
- **Fournisseurs** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter et des points d'accès personnalisés, avec vos propres clés.

## Vos données restent sur votre PC

Les conversations et les réglages sont stockés **uniquement sur votre machine**. Il n'existe aucun serveur ULTRAI — vos conversations ne partent que vers le fournisseur d'IA que vous avez vous-même connecté, avec votre propre clé.

Rien n'est collecté, et il n'y a aucune télémétrie.

## Démarrage rapide

1. **Connectez un fournisseur** — ajoutez votre clé API dans Réglages → Fournisseurs.
2. **Choisissez un modèle** — le modèle et l'effort de raisonnement se trouvent à droite de la barre de saisie.
3. **Choisissez un mode** — les onglets en haut de la barre latérale.
4. **Commencez à travailler** — ouvrez un dossier en mode Code ; dans les autres modes, il suffit de commencer à discuter.
5. **Déléguez une tâche** — dites « résume ma journée chaque soir » et l'application s'en chargera d'elle-même.

## Stack technique

Une application Windows native construite sur Tauri 2. L'interface est en SolidJS ; le backend s'exécute comme un binaire unique livré avec l'application.

## Retours

Les bugs et demandes de fonctionnalités se déposent dans les [Issues](https://github.com/UltraK18/ULTRAI/issues).

## Licence

ULTRAI est un logiciel gratuit (freeware). Gratuit pour un usage personnel et commercial. Le code source n'est pas disponible publiquement.

ULTRAI a commencé comme un fork d'[opencode](https://github.com/sst/opencode) et a été largement reconstruit depuis,
mais il inclut encore du code d'opencode, sous licence MIT — Copyright (c) 2025 opencode. La licence MIT est reproduite
intégralement dans les mentions légales fournies avec l'application.
