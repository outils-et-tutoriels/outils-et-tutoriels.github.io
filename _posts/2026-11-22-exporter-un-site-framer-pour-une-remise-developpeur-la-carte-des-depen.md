---
layout: post
title: "Exporter un site Framer pour une remise développeur : la carte des dépendances"
description: "Préparez un export Framer exploitable : séparez les fichiers statiques des services à reconnecter, puis remettez un dossier testable."
date: 2026-11-22 17:27:56 +0000
categories: [outils, tutoriels]
tags: [framer, export-statique, hebergement, remise-developpeur, exflow]
canonical_url: ""
image: "/assets/img/posts/2026-11-22-exporter-un-site-framer-pour-une-remise-developpeur-la-carte-des-depen/cover-eda7d341e2d0.webp"
---

# Exporter un site Framer pour une remise développeur : la carte des dépendances

Une copie statique de votre site Framer peut devenir un excellent dossier de remise — à condition de ne pas la confondre avec une copie de tous ses services. La bonne méthode consiste à exporter les pages, médias, polices et scripts, puis à isoler noir sur blanc ce qui doit être reconnecté : formulaires, mesure d’audience, e-mails et widgets. Avec cette carte, votre développeur reçoit un site testable au lieu d’un ZIP mystérieux.

[ExFlow pour Framer](https://exflow.site/framer) part d’une URL publiée et produit une copie statique avec HTML, CSS, JavaScript, polices et médias. Son intérêt ici n’est pas de promettre une migration magique : c’est de créer un point de départ tangible pour une reprise, un hébergement statique ou une sauvegarde vérifiable.

![Cartes illustrées représentant les services à reconnecter après un export Framer](/assets/img/posts/2026-11-22-exporter-un-site-framer-pour-une-remise-developpeur-la-carte-des-depen/image-01-8dec7a9a6826.webp)

## La règle simple : fichiers d’un côté, services de l’autre

Un export peut très bien conserver l’apparence d’une page tout en perdant une fonction qui vivait sur une plateforme distante. Framer documente d’ailleurs que le code personnalisé sert notamment aux balises d’analytics, aux pixels marketing, aux widgets de support, au CSS/JavaScript ajouté et aux données structurées : [la documentation officielle du code personnalisé](https://www.framer.com/help/articles/how-to-add-custom-code/) est donc un bon inventaire de départ.

Avant l’export, remplissez cette carte de dépendances :

| Élément | Reste dans les fichiers ? | Décision de remise |
| --- | --- | --- |
| Pages, images, vidéos, polices | En principe, oui | Ouvrir localement puis sur l’hébergement cible |
| Animations et composants client | Souvent, avec leurs scripts | Tester sur ordinateur et mobile ; noter les écarts |
| Formulaire de contact | Pas forcément | Choisir un endpoint ou un service de formulaires et faire un envoi réel |
| Analytics, pixels, chat | Non, si la balise ou le compte n’est pas repris | Lister l’identifiant, le propriétaire et le moment de réinstallation |
| Redirections et DNS | Non | Garder une table ancienne URL → nouvelle URL avant bascule |

Cette table n’a rien de bureaucratique : elle évite de livrer une page jolie dont le formulaire n’envoie plus rien. Le même réflexe est utile lors d’un [inventaire des dépendances Squarespace avant un export statique](https://outils-et-tutoriels.github.io/2026/11/06/comment-inventorier-les-dependances-squarespace-avant-un-export-statiq/) : le fichier livré et les services exploités sont deux périmètres différents.

## Préparer un export qui aide réellement la reprise

Commencez par figer une version publiée connue. Relevez l’URL de production, les pages importantes, les routes de CMS, les langues éventuelles et les zones protégées. Faites aussi une capture des réglages qui ne voyageront pas automatiquement : domaine, redirections, accès aux boîtes e-mail et comptes de mesure.

Ensuite, lancez l’export Framer dans ExFlow en gardant les fichiers CSS, JavaScript et médias. L’outil indique qu’il explore les pages publiées, récupère les ressources demandées par le navigateur et les relie localement ; vérifiez néanmoins le résultat comme un livrable, pas comme une sauvegarde aveugle. Téléchargez le ZIP pour un archivage local ou envoyez-le vers Git, S3 ou FTP si c’est le canal décidé avec l’équipe.

Le choix du canal importe moins que sa réversibilité. Un dépôt Git permet de dater le livrable et de comparer les versions. Un ZIP convenablement nommé est très utile pour une remise ponctuelle. Et si le but est un changement d’agence, gardez le site publié actif jusqu’à ce que la copie hébergée soit validée. Cette précaution rejoint le principe d’un [export Squarespace qui conserve les services utiles](https://outils-et-tutoriels.github.io/2026/11/13/exporter-un-site-squarespace-en-statique-sans-oublier-les-services-uti/) : on ne coupe pas l’existant parce qu’un dossier vient d’être téléchargé.

![Checklist illustrée pour tester routes, médias, polices et liens d’un export statique](/assets/img/posts/2026-11-22-exporter-un-site-framer-pour-une-remise-developpeur-la-carte-des-depen/image-02-a8a6629fbf03.webp)

## Le reçu de recette en cinq passages

Ouvrez la copie sur un serveur local ou, mieux, sur l’hébergement de préproduction. Puis testez les cinq passages ci-dessous, en notant une URL et un résultat pour chaque point.

1. **Routes.** Ouvrez l’accueil, trois pages profondes et une page CMS directement par leur URL. Vérifiez aussi le retour vers la navigation.
2. **Médias et polices.** Cherchez les images manquantes, les vidéos muettes et les titres qui changent de largeur. Une police absente peut dérégler une page entière.
3. **Mouvement.** Testez les interactions importantes : menu, accordéons, effets de défilement, état survolé et éléments mobiles. Ce sont les détails qui passent mal les tests trop rapides.
4. **Conversion.** Envoyez un formulaire vers le nouveau point de réception et vérifiez la boîte qui doit recevoir le message. Déclenchez les principaux événements analytics seulement après avoir réinstallé les balises autorisées.
5. **Référencement et liens.** Contrôlez titres, descriptions, images de partage, liens internes et redirections prioritaires. Une petite carte d’URLs rend ce contrôle plus efficace qu’une navigation au hasard.

Ne mélangez pas ce contrôle avec une retouche de contenu. Si une image ou une fiche doit changer, documentez-la dans un paquet séparé — comme dans notre méthode pour [remettre une photo produit retouchée sans ambiguïté](https://outils-et-tutoriels.github.io/2026/11/18/photo-produit-retouchee-le-paquet-de-livraison-qui-evite-les-malentend/). Vous saurez ainsi si un écart vient de l’export ou d’une modification éditoriale ultérieure.

## Ce que votre développeur doit recevoir

Le meilleur dossier de remise tient en une page : lien vers le dépôt ou archive, URL de préproduction, liste des services à reconnecter, coordonnées du propriétaire de chaque compte et critères de validation. Ajoutez une condition d’arrêt claire : « aucun changement DNS tant que formulaire, trois routes profondes, mobile et analytics ne sont pas validés ».

![Dossier de fichiers statiques relié à une infrastructure d’hébergement](/assets/img/posts/2026-11-22-exporter-un-site-framer-pour-une-remise-developpeur-la-carte-des-depen/image-03-043ac81160ad.webp)

Voici un modèle réutilisable :

> **Version source :** URL Framer et date de l’export  
> **Livrable :** ZIP ou dépôt, branche et révision  
> **Hébergement test :** URL de préproduction  
> **À reconnecter :** formulaire, analytics, pixel, chat, e-mail, redirections  
> **Preuve :** résultats des cinq passages de recette  
> **Feu vert :** personne responsable et condition de bascule

Cette fiche est aussi pratique pour un site e-commerce : une dépendance de catalogue mal recensée peut créer un écart difficile à expliquer, comme le montre notre guide pour [diagnostiquer un décalage entre Etsy, flux et Meta](https://outils-et-tutoriels.github.io/2026/11/22/catalogue-etsy-dans-meta-diagnostiquer-un-ecart-sans-tout-reimporter/).

## Une copie statique est un contrat de reprise

ExFlow peut accélérer la constitution du dossier, et il propose aussi des exporteurs dédiés à [Webflow](https://exflow.site/webflow) et à [Squarespace](https://exflow.site/squarespace). Mais l’outil ne remplace ni le choix d’un nouveau service de formulaire ni la validation du propriétaire des données.

Faites donc un premier export Framer, complétez la carte des dépendances, puis demandez une recette sur une URL de préproduction. C’est la prochaine action la plus simple pour transformer une copie de fichiers en remise réellement exploitable.
