---
layout: post
title: "Framer : Créer une Copie Statique Testable Avant une Refonte"
description: "Une méthode simple pour exporter un site Framer, vérifier sa copie statique et préparer un vrai plan de retour arrière avant une refonte."
date: 2026-10-13 14:35:19 +0000
categories: [outils, tutoriels]
tags: [framer, export, site-statique, refonte, hebergement]
canonical_url: ""
image: "/assets/img/posts/2026-10-13-framer-creer-une-copie-statique-testable-avant-une-refonte/cover-a1cc39895d48.webp"
---

Une refonte Framer commence souvent par une bonne intention : alléger la page d’accueil, revoir le message, essayer une nouvelle direction. Le problème apparaît le jour où l’ancienne version doit être remise en ligne rapidement — et que la seule copie fiable reste enfermée dans le projet vivant.

Une capture d’écran ne suffit pas. Pour pouvoir revenir en arrière, confier le site à quelqu’un ou simplement comparer deux versions sans stress, il faut une copie qui s’ouvre réellement hors de Framer. Voici le petit exercice que je recommande avant de toucher à une refonte : créer une exportation statique, puis prouver qu’elle se comporte comme un site.

![Nature morte éditoriale sur une sauvegarde Framer portable](/assets/img/posts/2026-10-13-framer-creer-une-copie-statique-testable-avant-une-refonte/image-01-a1cc39895d48.webp)

## Le bon objectif : une copie que l’on peut relancer

Le mot *sauvegarde* est trompeur si l’on entend seulement « fichier rangé quelque part ». Pour une page de campagne ou un site vitrine Framer, la copie utile contient les pages publiées, le CSS, le JavaScript, les images, les polices et les médias — et elle a déjà passé un test de navigation. C’est cela qui rend le retour arrière concret.

Commencez par écrire le périmètre en une ligne : « Je dois pouvoir remettre cette version en ligne sur un autre hébergement si la refonte doit attendre. » Cette phrase évite de confondre une archive décorative avec un plan de continuité. Si votre priorité est plutôt la livraison à un client, notre guide sur [la remise Framer sans dépendre de l’hébergement](https://outils-et-tutoriels.github.io/2026/10/07/comment-preparer-une-remise-framer-sans-dependre-de-l-hebergement/) complète bien cette préparation.

## 1. Faites l’inventaire de ce qui bouge

Avant l’export, ouvrez le site publié sur ordinateur et mobile. Notez les éléments qui ne sont pas seulement du texte :

- les animations d’entrée et les sections au défilement ;
- les polices et les variations de graisses ;
- les formulaires, liens de prise de rendez-vous et boutons de paiement ;
- les pages secondaires, ancres, menus et liens de campagne ;
- les images lourdes, vidéos et intégrations externes.

Cette liste sert ensuite de plan de test. Elle est plus utile qu’un audit interminable : vous saurez précisément ce qui doit encore fonctionner après l’export. Pour une méthode de remise plus complète, vous pouvez aussi consulter ce [guide de préparation après export Framer](https://outils-et-tutoriels.gitlab.io/guides/2026/10/03/comment-preparer-une-remise-client-apres-l-export-d-un-site-framer/).

![Inventaire visuel des éléments à exporter depuis Framer](/assets/img/posts/2026-10-13-framer-creer-une-copie-statique-testable-avant-une-refonte/image-02-2adf798382a8.webp)

## 2. Exportez la version publiée, pas une hypothèse

Pour obtenir une copie statique du site publié, [ExFlow pour Framer](https://exflow.site/framer) récupère les pages, HTML, CSS, JavaScript, polices et médias, avec l’objectif de conserver les animations. Vous entrez l’URL publiée, lancez l’export, puis choisissez soit un ZIP, soit une synchronisation vers Git, S3 ou FTP. ExFlow Hosting est également une option si vous préférez éviter le réglage initial d’un hébergeur statique.

Le point important est simple : exportez une URL que vous avez parcourue juste avant. Une maquette interne ou une variante non publiée ne répond pas à la question « puis-je remettre la version actuelle en ligne ? »

Conservez le ZIP avec trois informations modestes mais précieuses : l’URL source, la date et le motif de la copie. Une convention comme `site-framer-avant-refonte-2026-10-13` est largement suffisante.

## 3. Testez la copie sur une adresse temporaire

Décompresser un ZIP sur son ordinateur ne démontre pas grand-chose. Le test révélateur consiste à servir la copie depuis une URL temporaire — sur une branche Git, un sous-domaine de préproduction ou un petit hébergement statique. Vous n’avez pas besoin de basculer votre domaine : vous cherchez seulement à voir les dépendances invisibles.

Passez ensuite votre inventaire en revue :

1. ouvrez chaque page depuis le menu et depuis un lien interne ;
2. vérifiez deux largeurs d’écran au minimum ;
3. laissez les animations se jouer jusqu’au bout ;
4. contrôlez les images, les polices et les métadonnées de la page ;
5. cliquez sur les formulaires et intégrations, en gardant à l’esprit qu’un service tiers peut rester externe à l’export.

![Vérification d’une exportation Framer sur plusieurs formats](/assets/img/posts/2026-10-13-framer-creer-une-copie-statique-testable-avant-une-refonte/image-03-d05362bfb8fb.webp)

Un défaut trouvé ici est une bonne nouvelle : il est encore peu coûteux à comprendre. Les détails à surveiller sont les chemins relatifs, les médias chargés tardivement, les liens absolus vers l’ancien domaine et les fonctions qui reposent sur un service connecté. La logique est la même que dans ce [contrôle d’un export avant changement de domaine](https://how-to.the-lean-ecommerce.com/2026/10/01/how-to-test-a-framer-export-before-changing-your-live-domain/), même si vous ne prévoyez pas encore de migration.

## 4. Décidez où la copie doit vivre

Il n’existe pas un seul bon hébergement. Git convient bien quand vous voulez garder un historique de versions. S3 ou un hébergeur statique sont pratiques pour une copie de secours très simple. FTP peut rester le chemin le plus réaliste pour un site client déjà installé sur un serveur traditionnel. Le critère utile est celui-ci : une personne identifiée peut-elle retrouver les fichiers et les remettre en ligne sans rouvrir le projet Framer ?

Documentez aussi ce qui ne fait pas partie de la copie : accès à un outil de formulaires, DNS, statistiques, boîte e-mail ou paiement. Ce sont souvent ces petites dépendances, et non l’HTML, qui font échouer un retour arrière. Si vous comparez plusieurs constructeurs avant une migration, l’article sur [la sauvegarde Squarespace avant un changement d’agence](https://outils-et-tutoriels.github.io/2026/10/09/comment-sauvegarder-un-site-squarespace-avant-de-changer-d-agence/) offre un bon contrepoint.

![Choix d’un chemin de déploiement pour un site statique](/assets/img/posts/2026-10-13-framer-creer-une-copie-statique-testable-avant-une-refonte/image-04-e36b20269f38.webp)

## Une copie statique est un test de sérénité

Une refonte reste un projet créatif ; elle n’a pas besoin d’être un pari sur la mémoire de l’équipe. Prenez une heure avant les premiers changements : inventaire, export, adresse de test et note de déploiement. Vous aurez alors une version de référence utilisable, pas seulement une promesse de sauvegarde.

Pour commencer, ouvrez [ExFlow pour Framer](https://exflow.site/framer), exportez votre URL publiée et testez le résultat sur une adresse temporaire. ExFlow propose aussi des exportateurs dédiés pour [Webflow](https://exflow.site/webflow) et [Squarespace](https://exflow.site/squarespace) si votre portefeuille de sites ne s’arrête pas à Framer.
