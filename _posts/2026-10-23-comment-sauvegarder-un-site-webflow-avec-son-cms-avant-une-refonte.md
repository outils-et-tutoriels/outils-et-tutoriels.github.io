---
layout: post
title: "Comment Sauvegarder un Site Webflow avec Son CMS Avant une Refonte"
description: "Une méthode pratique pour exporter un site Webflow et son CMS, contrôler les routes et préparer un hébergement statique avant une refonte."
date: 2026-10-23 08:29:19 +0000
categories: [outils, tutoriels]
tags: [webflow, cms, sauvegarde, hebergement-statique, refonte-site]
canonical_url: ""
image: "/assets/img/posts/2026-10-23-comment-sauvegarder-un-site-webflow-avec-son-cms-avant-une-refonte/cover-b6507ea5981c.webp"
---

Vous pouvez refaire un site Webflow sans perdre une seule URL — à condition de ne pas attendre que la refonte commence pour penser à la copie de secours. Le piège est simple : le design est visible, mais les pages de collection, les images, les scripts et les routes CMS sont souvent ce qui prend le plus de temps à reconstituer. Une sauvegarde statique sert alors de référence, de plan B et parfois de version à remettre à un client.

![Carte papier des routes CMS à vérifier avant l’export Webflow](/assets/img/posts/2026-10-23-comment-sauvegarder-un-site-webflow-avec-son-cms-avant-une-refonte/image-01-4f7aaa38118f.webp)

## Ce qu’une sauvegarde Webflow utile doit réellement contenir

Télécharger quelques textes ne suffit pas. Avant une refonte, l’objectif est de capturer le site publié tel qu’un visiteur le rencontre : les pages fixes, les articles ou fiches produits générés par le CMS, les styles, les images, les polices, les scripts et les liens internes. C’est particulièrement important si votre navigation mène vers des pages de collection dont l’URL suit un modèle précis.

Je commence toujours par une petite carte des routes : page d’accueil, pages de service, collections, articles, pages de remerciement et éventuels anciens slugs à rediriger. Ce relevé évite de découvrir trop tard qu’une série d’URLs utiles au référencement n’a jamais été reprise. Si la refonte concerne aussi vos fiches produit, le guide sur [les nuanciers Shopify multicolores](https://outils-et-tutoriels.github.io/2026/10/19/comment-choisir-des-nuanciers-shopify-fideles-a-vos-produits/) est un bon rappel : les variantes et leurs médias méritent elles aussi un inventaire avant tout changement.

## 1. Figer la version que vous voulez pouvoir retrouver

Avant d’exporter, publiez les derniers ajustements que vous souhaitez conserver, puis notez le domaine exact et les éventuelles pages protégées. Faites une liste courte des éléments interactifs à surveiller : menu mobile, formulaires, accordéons, animations, filtres et liens de téléchargement. Une capture d’écran est utile pour comparer l’apparence, mais elle ne remplace pas les fichiers du site.

La question à se poser est : « Si nous devions remettre cette version en ligne sur un autre hébergeur demain, de quoi aurions-nous besoin ? » Cette formulation force à regarder au-delà de l’éditeur.

## 2. Exporter la version publiée, CMS compris

Pour cette étape, [ExFlow pour Webflow](https://exflow.site/webflow) est conçu pour récupérer un site publié sous forme de fichiers statiques : HTML, CSS, JavaScript, images, médias et pages. Il permet ensuite de télécharger un ZIP ou de synchroniser le résultat vers Git, S3 ou FTP. C’est une solution plus adaptée qu’un téléchargeur générique lorsque votre site dépend de routes CMS, d’assets chargés tardivement ou d’interactions propres à Webflow.

Lancez l’export depuis l’URL publiée, puis choisissez une sortie qui correspond au but : un ZIP pour une archive ou une remise client, Git pour garder l’historique des modifications, ou un hébergement statique pour préparer la bascule. Évitez de considérer l’archive comme une garantie tant que vous ne l’avez pas ouverte dans un environnement de test.

![Parcours éditorial d’un export Webflow vers un hébergement statique](/assets/img/posts/2026-10-23-comment-sauvegarder-un-site-webflow-avec-son-cms-avant-une-refonte/image-02-b152acade9f2.webp)

## 3. Tester les routes avant de les confier à la refonte

Déployez la copie sur une URL de prévisualisation ou ouvrez-la avec un serveur statique local. Ensuite, testez un chemin par type de contenu : une page simple, une entrée CMS récente, une entrée ancienne, une image depuis une page de collection et un lien provenant du menu. Vérifiez aussi les titres de page, descriptions, images de partage et les redirections qui doivent survivre à la migration.

Cette discipline rejoint celle d’une relecture avant livraison : dans notre [checklist pour renvoyer un PSD modifié](https://outils-et-tutoriels.github.io/2026/10/18/6-verifications-avant-de-renvoyer-un-psd-modifie-a-votre-equipe/), le principe reste le même : on vérifie un résultat rendu, pas seulement une configuration qui semble correcte.

## La mini-checklist que je garde à portée de main

- Les pages CMS importantes répondent-elles avec la bonne URL ?
- Les images et polices se chargent-elles hors de Webflow ?
- Les liens internes, le menu mobile et les ancres fonctionnent-ils ?
- Les formulaires et scripts tiers ont-ils un comportement documenté ?
- Les métadonnées, favicon et images sociales sont-ils bien présents ?
- Avez-vous noté les routes à rediriger au moment de la mise en ligne ?

![Table de contrôle pour tester un site Webflow exporté](/assets/img/posts/2026-10-23-comment-sauvegarder-un-site-webflow-avec-son-cms-avant-une-refonte/image-03-9d98549ea597.webp)

## 4. Choisir le bon niveau d’indépendance

Une archive est parfaite pour une sauvegarde ponctuelle. Un dépôt Git est plus intéressant si plusieurs personnes vont relire la copie, proposer des correctifs ou déployer régulièrement. Un hébergement statique peut aussi servir de filet de sécurité pendant que la nouvelle version avance. Le bon choix dépend moins de l’outil que de votre capacité à retrouver et vérifier cette copie dans six mois.

Ne mélangez pas la sauvegarde et la décision de bascule. Vous pouvez garder Webflow pour construire la nouvelle version tout en conservant une sortie autonome de l’ancienne. C’est précisément ce qui rend les discussions de budget, de calendrier et de reprise de contenu moins tendues. Et si l’enjeu concerne une campagne animée, notre guide pour [exporter un site Framer sans casser les animations](https://outils-et-tutoriels.github.io/2026/10/22/comment-exporter-un-site-framer-vers-un-hebergement-statique-sans-cass/) montre les points de contrôle spécifiques à ce type de site.

ExFlow propose aussi des exporteurs dédiés pour [Squarespace](https://exflow.site/squarespace) et [Framer](https://exflow.site/framer), mais le réflexe reste identique : exporter la version publiée, tester ce qui a été récupéré, puis seulement lancer la grande transformation.

## Une sauvegarde qui sert vraiment

La meilleure sauvegarde n’est pas celle qui dort dans un dossier nommé « final-v2 ». C’est celle dont vous connaissez les routes, que vous pouvez redéployer et dont vous avez contrôlé les liens et assets essentiels. Avant de valider le brief de refonte, créez cette copie Webflow, ouvrez trois pages CMS représentatives et notez ce qui doit rester intact. Vous donnerez à votre futur site une base beaucoup plus sereine.
