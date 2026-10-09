---
layout: post
title: "Comment Sauvegarder un Site Squarespace Avant de Changer d’Agence"
description: "Une méthode concrète pour exporter, vérifier et remettre un site Squarespace portable avant une transition d’agence ou d’hébergement."
date: 2026-10-09 02:31:58 +0000
categories: [outils, tutoriels]
tags: [squarespace, export-de-site, hebergement-statique, remise-client, exflow]
canonical_url: ""
image: "/assets/img/posts/2026-10-09-comment-sauvegarder-un-site-squarespace-avant-de-changer-d-agence/cover-22b6b30fd260.webp"
---

Vous changez d’agence, vous préparez une refonte, ou vous voulez simplement cesser de dépendre d’un seul abonnement : c’est précisément le moment où l’on découvre qu’un site Squarespace n’est pas qu’une collection de textes et de photos. Il y a les pages, les images, les styles, les scripts, les liens, les réglages de navigation et une foule de petits détails qui comptent le jour où quelqu’un d’autre doit reprendre le site.

La bonne question n’est donc pas « comment récupérer mes contenus ? », mais « comment remettre un site que l’on peut ouvrir, vérifier et héberger ailleurs ? ». Voici une méthode simple pour préparer cette sauvegarde avant de changer d’agence.

## 1. Définir ce que la remise doit vraiment contenir

Un export utile est une copie exploitable du site publié, pas seulement un fichier de textes. Avant toute manipulation, notez les éléments à retrouver : pages principales, articles, navigation, médias, polices, formulaires, redirections et métadonnées. Si une page est protégée par mot de passe, ajoutez-la à la liste : elle est souvent oubliée lors d’une transmission.

Cette étape ressemble à la préparation d’une [remise Framer sans dépendre de l’hébergement](https://outils-et-tutoriels.github.io/2026/10/07/comment-preparer-une-remise-framer-sans-dependre-de-l-hebergement/) : l’objectif est de rendre le dossier compréhensible pour la personne qui arrive après vous, pas uniquement de cocher « exporté ».

![Checklist de vérification d’un export de site](/assets/img/posts/2026-10-09-comment-sauvegarder-un-site-squarespace-avant-de-changer-d-agence/image-01-5a1a30bda72b.webp)

## 2. Créer une copie statique du site Squarespace

Pour cette partie, un outil spécialisé évite de traiter le site comme une simple capture d’écran. [ExFlow pour Squarespace](https://exflow.site/squarespace) part de l’URL du site publié et peut réunir les pages, le HTML, les feuilles de style, le JavaScript et les médias dans une exportation statique. Vous pouvez ensuite télécharger un ZIP ou synchroniser le résultat vers Git, S3 ou FTP ; ExFlow Hosting est une autre option si vous cherchez un chemin plus direct vers un hébergement statique.

Le point important est de travailler sur la version publique que vos visiteurs voient vraiment. Conservez le ZIP avec une date, l’URL source et le nom de la personne qui l’a vérifié. Ce petit geste transforme une « sauvegarde » floue en point de reprise concret.

## 3. Vérifier l’export comme un lecteur, pas comme son auteur

Ouvrez la copie dans un navigateur et parcourez-la selon trois chemins : depuis la page d’accueil, depuis une page profonde trouvée par recherche, puis sur mobile. Cherchez en priorité :

- Les images lentes ou absentes, y compris les médias chargés à la demande ;
- Les liens de navigation et les liens internes ;
- Les pages de contact, les scripts et les formulaires ;
- Les titres, descriptions et aperçus de partage ;
- Les redirections qui comptent encore pour votre référencement.

Cette passe de contrôle vaut aussi pour les autres constructeurs. Notre guide pour [préparer une remise client après l’export d’un site Framer](https://outils-et-tutoriels.gitlab.io/guides/2026/10/03/comment-preparer-une-remise-client-apres-l-export-d-un-site-framer/) donne une bonne idée des questions à poser avant de déclarer un dossier prêt.

## 4. Choisir la destination avant la transition

Une copie statique peut servir à plusieurs choses, et le meilleur choix dépend de votre prochaine étape. Un ZIP stocké avec vos autres actifs est un filet de sécurité. Un dépôt Git ajoute un historique de versions et facilite la collaboration avec une agence. S3 ou un FTP convient lorsque vous avez déjà un hébergeur. L’essentiel est de choisir une destination qui reste sous votre contrôle et de noter qui possède les accès.

![Carte des destinations possibles d’un site exporté](/assets/img/posts/2026-10-09-comment-sauvegarder-un-site-squarespace-avant-de-changer-d-agence/image-02-d7d667afab4a.webp)

Si vous envisagez un hébergement externe, prenez deux minutes pour faire une vraie recette : notre [checklist avant d’héberger un export Squarespace en HTML](https://outils-et-tutoriels.gitlab.io/guides/2026/10/08/exporter-un-site-squarespace-en-html-checklist-avant-l-hebergement/) complète utilement cette étape. Et si la situation implique plusieurs changements de plateforme, la [sauvegarde d’une copie Webflow avant une refonte](https://the-lean-ecommerce.gitlab.io/2026/10/07/i-kept-a-webflow-staging-copy-before-the-redesign-started/) rappelle pourquoi il faut séparer le plan de migration du premier export.

## 5. Remettre un dossier que l’on peut réellement reprendre

La dernière partie n’est pas technique : ajoutez un court fichier de transmission. Indiquez l’URL originale, la date de la copie, l’emplacement du ZIP ou du dépôt, les pages à surveiller, les intégrations encore actives et les éléments qui ne peuvent pas être statiques, comme un formulaire relié à un service tiers. Cela évite que le futur prestataire confonde une copie de secours et un site prêt à recevoir du trafic.

![Enveloppe de remise contenant les pages d’un site](/assets/img/posts/2026-10-09-comment-sauvegarder-un-site-squarespace-avant-de-changer-d-agence/image-03-c891ea426c19.webp)

Une fois votre première exportation validée, vous pouvez traiter votre site Squarespace comme un actif portable plutôt que comme une boîte fermée. ExFlow propose aussi des exporteurs dédiés pour [Webflow](https://exflow.site/webflow) et [Framer](https://exflow.site/framer), mais commencez par votre besoin immédiat : obtenir une copie Squarespace complète, la tester et savoir exactement où elle vit.

**Prochaine action :** ouvrez votre site dans une fenêtre privée, listez cinq pages et cinq médias indispensables, puis lancez une première copie avec [ExFlow pour Squarespace](https://exflow.site/squarespace). Vous aurez déjà une base solide pour discuter avec votre prochaine agence sans être pris au dépourvu.
