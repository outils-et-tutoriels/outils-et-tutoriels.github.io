---
layout: post
title: "Comment garder une copie statique utile de son site Squarespace"
description: "Une methode simple pour exporter un site Squarespace, tester les fichiers et preparer une vraie copie de secours."
date: 2026-09-15 16:23:14 +0000
categories: [outils, site-web]
tags: [squarespace, export, site-statique]
canonical_url: ""
image: "/assets/img/posts/2026-09-15-comment-garder-une-copie-statique-utile-de-son-site-squarespace/cover-cfcf401b7673.webp"
---

## Une sauvegarde de site doit pouvoir s ouvrir

Un export de contenu ne remplace pas une copie du site que les visiteurs voient. Quand un renouvellement, une refonte ou un passage de relais approche, je cherche une version statique qui conserve les pages, styles, scripts et medias utiles.

[ExFlow pour Squarespace](https://exflow.site/squarespace) permet d exporter un site publie en HTML, CSS, JavaScript et medias, puis de recuperer un ZIP ou de le diriger vers Git, S3, FTP ou un hebergement gere.

![Archive statique Squarespace](/assets/img/posts/2026-09-15-comment-garder-une-copie-statique-utile-de-son-site-squarespace/image-01-cfcf401b7673.webp)

## 1. Noter les pages qui comptent

Avant l export, listez l accueil, les pages de vente, les pages de confirmation et les liens venant de campagnes. Notez aussi les fonctions externes comme les formulaires ou analytics: une copie statique ne les remplace pas automatiquement.

![Configuration d un export ExFlow](/assets/img/posts/2026-09-15-comment-garder-une-copie-statique-utile-de-son-site-squarespace/image-02-f880d85dfc87.webp)

## 2. Exporter puis tester hors de Squarespace

Une fois les fichiers obtenus, ouvrez les pages directement, pas seulement la page d accueil. Verifiez les images, navigation, liens internes, metas et affichage mobile. Une archive utile est une archive que quelqu un d autre peut ouvrir sans deviner le contexte.

![Fichiers generes apres export](/assets/img/posts/2026-09-15-comment-garder-une-copie-statique-utile-de-son-site-squarespace/image-03-f0a1e1900dd6.webp)

## 3. Choisir le bon emplacement

Un ZIP convient pour une sauvegarde. Un depot Git convient mieux quand les fichiers doivent garder un historique. S3 ou FTP peuvent correspondre a une infrastructure existante; ExFlow Hosting est une option plus directe. Gardez pres des fichiers l URL source, la date et les elements qui demandent une action speciale.

Pour une prochaine refonte, commencez par [l exporteur Squarespace](https://exflow.site/squarespace), puis ouvrez la copie sur un hebergement temporaire avant de considerer le travail termine.
