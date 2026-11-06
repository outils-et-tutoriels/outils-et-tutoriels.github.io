---
layout: post
title: "Comment inventorier les dépendances Squarespace avant un export statique"
description: "Avant de déplacer un site Squarespace, repérez formulaires, paiements, recherche et services externes pour préparer un export statique fiable."
date: 2026-11-06 17:34:53 +0000
categories: [outils, tutoriels]
tags: [squarespace, hebergement-statique, migration-de-site, sauvegarde, exflow]
canonical_url: ""
image: "/assets/img/posts/2026-11-06-comment-inventorier-les-dependances-squarespace-avant-un-export-statiq/cover-d461c3e36ca4.webp"
---

# Comment inventorier les dépendances Squarespace avant un export statique

Exporter un site Squarespace en fichiers statiques peut préserver ce que vos visiteurs voient, mais pas automatiquement ce qui se passe côté serveur. Avant de changer d’hébergement, listez chaque formulaire, paiement, espace membre, recherche et script externe ; vous saurez ainsi ce qui peut suivre l’export et ce qui doit être remplacé.

C’est une étape courte, mais elle évite le pire scénario de remise : un site visuellement impeccable dont le formulaire de contact ou la prise de rendez-vous a silencieusement cessé de fonctionner. Si votre objectif est d’obtenir une copie complète du site publié, [l’exporteur Squarespace d’ExFlow](https://exflow.site/squarespace) récupère les pages, styles, scripts et médias servis par le site ; l’inventaire ci-dessous vous aide à décider ce qui vient ensuite.

## Pourquoi faire l’inventaire avant l’export

Une exportation statique répond très bien aux besoins de sauvegarde, de remise à un client, de prévisualisation ou d’hébergement indépendant. Elle ne transforme pas des fonctionnalités gérées par Squarespace en services autonomes. Autrement dit : le contenu et l’interface peuvent voyager, tandis qu’un service qui enregistre des données ou demande une connexion doit avoir un nouveau point d’arrivée.

La différence est importante pour une petite équipe. Un bouton qui affiche une page, une galerie ou un PDF est généralement un élément à vérifier. Un bouton qui collecte un message, lance un paiement ou consulte une base de données est une dépendance à décider. Pour organiser la copie de secours elle-même, vous pouvez compléter ce travail avec [cette méthode de sauvegarde Squarespace avant un changement d’agence](https://outils-et-tutoriels.github.io/2026/10/09/comment-sauvegarder-un-site-squarespace-avant-de-changer-d-agence/).

![Cartes de dépendances à remplacer lors d’une sortie statique](/assets/img/posts/2026-11-06-comment-inventorier-les-dependances-squarespace-avant-un-export-statiq/image-01-4ae23d6480e0.webp)

## Le relevé en quatre colonnes

Ouvrez le site publié dans un navigateur normal et parcourez les parcours qu’un visiteur suit réellement : arrivée, découverte, prise de contact, achat ou demande de rendez-vous. Pour chaque élément actif, notez quatre choses :

| Élément observé | Peut rester statique ? | Décision avant mise en ligne | Test à prévoir |
| --- | --- | --- | --- |
| Pages, articles, galeries, fichiers téléchargeables | Oui, le plus souvent | Vérifier les URL et les médias locaux | Ouvrir les pages depuis le nouvel hébergeur |
| Formulaire de contact ou newsletter | Non, pas seul | Repointer vers un service de formulaire ou votre endpoint | Envoyer un vrai message et vérifier sa réception |
| Boutique et paiement | Non | Conserver/brancher une solution commerce adaptée | Parcourir le tunnel sans simuler de commande réelle |
| Recherche, espace membre, réservation | Non | Choisir un remplacement ou retirer clairement la fonction | Tester avec un compte ou une requête représentative |
| Analytics, pixels, chat, carte, vidéo embarquée | Cela dépend | Conserver le script si les règles de confidentialité et le fournisseur le permettent | Vérifier console, consentement et rendu mobile |

Ne confondez pas « présent dans le code » et « utile ». Un ancien pixel, un formulaire de campagne terminé ou un widget de chat abandonné mérite souvent d’être supprimé, pas déplacé. L’inventaire est aussi une occasion de réduire les dépendances que personne ne veut maintenir.

## Ce qu’un export peut conserver — et ce qu’il ne remplace pas

ExFlow décrit son export Squarespace comme une capture du site publié : HTML rendu, CSS, JavaScript, images, médias, polices et autres ressources publiques, avec des liens réécrits vers les fichiers locaux. Vous pouvez télécharger l’archive ou l’envoyer vers Git, S3, FTP ou un hébergement statique. Les sites protégés par mot de passe peuvent aussi être exportés si vous fournissez le mot de passe frontal.

En revanche, ExFlow précise que les soumissions de formulaires, le checkout Squarespace Commerce, les espaces membres, la prise de rendez-vous et la recherche côté Squarespace ne sont pas transportés comme services fonctionnels. Ce ne sont pas des défauts cachés : ce sont des services serveur à traiter dans votre plan de migration. La même vigilance sert quand on remplace des fonctions actives d’un autre constructeur, comme dans ce guide pour [préparer formulaires et analytics Framer avant un hébergement statique](https://outils-et-tutoriels.github.io/2026/11/04/exporter-un-site-framer-remplacer-son-formulaire-avant-l-hebergement-s/).

## Une procédure courte et réutilisable

1. **Figez le périmètre.** Notez l’URL de production, la date, les langues et les pages qui doivent absolument rester accessibles. Ne vous contentez pas de la page d’accueil.
2. **Parcourez les actions.** Cliquez sur chaque appel à l’action, testez la recherche, remplissez un formulaire de test et suivez les liens de navigation mobile. Ajoutez chaque interaction active à votre relevé.
3. **Classez chaque dépendance.** Marquez-la « conserver », « remplacer », « retirer » ou « hors périmètre ». Si elle collecte une donnée personnelle, ajoutez le propriétaire responsable et le canal de réception.
4. **Lancez une exportation de test.** Avec ExFlow, activez les pages, CSS, JavaScript et médias ; choisissez aussi toutes les pages si votre objectif couvre le site entier. Gardez l’archive datée : elle devient votre référence de départ.
5. **Déployez loin du domaine principal.** Un sous-domaine de préproduction ou une URL temporaire est préférable. Vous évitez de modifier DNS ou référencement avant d’avoir obtenu des preuves.
6. **Testez la copie comme un visiteur.** Vérifiez les liens, médias, police, menu, galerie, aperçu mobile, métadonnées, redirections prévues et chaque remplacement de dépendance.

![Contrôles de qualité pour vérifier les fichiers d’un site statique](/assets/img/posts/2026-11-06-comment-inventorier-les-dependances-squarespace-avant-un-export-statiq/image-02-6e127e7cdaf7.webp)

## Le contrôle de sortie qui évite les faux positifs

Une page peut sembler correcte sur votre ordinateur tout en échouant ailleurs à cause d’un chemin absolu, d’un script tiers refusé ou d’une police non chargée. Faites donc le dernier contrôle dans une fenêtre privée et sur un téléphone. Gardez une petite fiche avec l’URL testée, le résultat et le responsable de la correction.

Deux signaux doivent vous faire suspendre le basculement : un parcours de contact ou de vente sans destination confirmée, et une ressource essentielle chargée depuis l’ancien domaine sans raison claire. Dans les deux cas, le design peut attendre ; l’usage réel ne doit pas être laissé au hasard. Cette logique de gel et de validation rejoint aussi [la façon de garder des fiches CMS Webflow incomplètes hors publication](https://outils-et-tutoriels.github.io/2026/11/06/synchroniser-notion-vers-webflow-sans-publier-des-fiches-incompletes/).

## Préparer une remise qui reste exploitable

À la fin, transmettez davantage qu’un ZIP : la date de l’export, l’URL de test, la destination d’hébergement, la liste des services remplacés, les accès détenus par le client et les limites connues. C’est ce qui permet à quelqu’un d’autre de reprendre le site sans deviner.

Si votre site est surtout public et éditorial, un export statique peut être une excellente manière de récupérer de la portabilité sans tout reconstruire. ExFlow propose aussi des exporteurs dédiés pour [Webflow](https://exflow.site/webflow) et [Framer](https://exflow.site/framer), mais commencez par le constructeur qui héberge réellement votre site : les dépendances à vérifier ne sont jamais tout à fait les mêmes.

![Dossier de livraison pour un site web statique](/assets/img/posts/2026-11-06-comment-inventorier-les-dependances-squarespace-avant-un-export-statiq/image-03-c5baab177f19.webp)

L’action suivante est simple : ouvrez votre site Squarespace, notez cinq interactions qui comptent pour vos visiteurs, puis donnez à chacune une décision avant de générer la première archive. Vous saurez alors si vous préparez une vraie remise — ou seulement une jolie capture d’écran.
