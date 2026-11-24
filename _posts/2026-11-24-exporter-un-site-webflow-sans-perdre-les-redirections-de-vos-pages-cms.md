---
layout: post
title: "Exporter un site Webflow sans perdre les redirections de vos pages CMS"
description: "Préparez un registre de redirections, exportez votre site Webflow en statique et vérifiez les anciennes URLs avant la bascule."
date: 2026-11-24 08:32:47 +0000
categories: [outils, tutoriels]
tags: [webflow, export-statique, redirections, cms, hebergement]
canonical_url: ""
image: "/assets/img/posts/2026-11-24-exporter-un-site-webflow-sans-perdre-les-redirections-de-vos-pages-cms/cover-4c2ab007a508.webp"
---

# Exporter un site Webflow sans perdre les redirections de vos pages CMS

Quand vous passez un site Webflow sur un hébergement statique, l’export des fichiers n’est qu’une moitié du travail : il faut aussi préserver le chemin des visiteurs arrivant sur vos anciennes pages CMS. La méthode la plus sûre consiste à établir un registre `ancienne URL → URL finale`, à le traduire dans la configuration de votre nouvel hébergeur, puis à tester chaque chemin avant et après la bascule.

C’est particulièrement important pour un blog, un catalogue ou un annuaire : les URLs d’anciens articles continuent de vivre dans Google, les favoris, les campagnes et les liens de partenaires. Une belle copie statique qui répond 404 à ces entrées perd une partie de sa valeur au premier jour. Pour récupérer les pages, styles, scripts, médias et routes publiées, un [export Webflow avec ExFlow](https://exflow.site/webflow) peut fournir une base de fichiers à contrôler et à déployer. Il ne remplace pas la règle de redirection de votre hébergeur : c’est précisément pourquoi il faut préparer les deux ensemble.

![Registre de redirections avec chemins source et destination](/assets/img/posts/2026-11-24-exporter-un-site-webflow-sans-perdre-les-redirections-de-vos-pages-cms/image-01-16c7bf69461d.webp)

## Le registre de redirections : un petit livrable qui évite les grandes pertes

Je ne pars pas d’une liste de pages « à peu près importantes ». Je prépare un tableau avec cinq colonnes :

| Ancien chemin | URL finale attendue | Type | Priorité | Test effectué |
| --- | --- | --- | --- | --- |
| `/blog/nom-article` | `/ressources/nom-article/` | 301 permanent | haute | oui/non |
| `/produits/ancien-modele` | `/produits/nouveau-modele/` | 301 permanent | haute | oui/non |
| `/categorie/ancien-sujet` | `/guides/` | décision éditoriale | moyenne | oui/non |

Le mot important est **finale**. Une redirection ne doit pas envoyer vers une URL qui redirige encore, ni vers une page vaguement voisine. Si une page n’a pas d’équivalent honnête, je préfère une page de catégorie pertinente ou une 404 utile avec navigation, plutôt qu’un détour trompeur vers l’accueil.

Webflow indique qu’une 301 sert à diriger durablement une ancienne adresse vers une nouvelle et recommande de vérifier le résultat dans un nouvel onglet. Sa documentation précise aussi que les règles sont exécutées dans leur ordre de création : les règles précises doivent donc précéder les règles globales. Gardez cette contrainte quand vous transcrivez la liste chez votre futur hébergeur. [Le guide Webflow sur les redirections 301](https://help.webflow.com/hc/en-us/articles/33961294898835-How-do-I-set-up-redirects-in-Webflow) donne aussi les cas particuliers, notamment les groupes de capture et les caractères à échapper.

## Choisir ce qui doit figurer dans la liste

Avant l’export, rassemblez les chemins depuis quatre endroits : votre sitemap, les collections CMS, les rapports d’erreurs 404 et les liens utilisés dans vos campagnes. Pour les collections, ne retenez pas seulement le modèle d’URL : prenez des exemples réels de fiches, dont une ancienne, une récente et une avec un slug contenant un tiret ou un accent.

Ajoutez ensuite les pages qui changent souvent lors d’une refonte : pages de campagne, catégories, anciennes pages d’équipe et pages de téléchargement. Cette préparation complète bien une [carte des dépendances pour une remise Framer](https://outils-et-tutoriels.github.io/2026/11/22/exporter-un-site-framer-pour-une-remise-developpeur-la-carte-des-depen/) : le principe reste le même, mais ici le résultat recherché est une destination HTTP exacte pour chaque entrée utile.

## Exporter sans confondre fichiers et comportement serveur

Une exportation statique récupère le contenu qui doit être servi : HTML, CSS, JavaScript, images, médias et pages publiées. Avec ExFlow, le point de départ est l’URL publiée du site ; vous pouvez ensuite télécharger une archive ou synchroniser le résultat vers Git, S3 ou FTP. L’export est donc une bonne occasion de vérifier que les routes CMS attendues existent réellement dans le dossier ou dans l’aperçu de déploiement.

Mais un dossier ne sait pas, à lui seul, répondre « cette ancienne URL doit aller là ». Il faut configurer les redirections dans la couche qui reçoit les requêtes : fichier de règles de l’hébergeur, configuration CDN ou plateforme de déploiement. Gardez le registre dans le dépôt, près des règles, afin qu’une modification de slug ne devienne pas une connaissance perdue dans une feuille isolée.

Cette distinction évite aussi un faux sentiment de sécurité. Lors d’un précédent contrôle de site, le bon réflexe était de [tester une copie statique Squarespace avant la bascule](https://how-to.the-lean-ecommerce.com/2026/11/07/how-to-test-a-squarespace-static-copy-before-a-github-pages-cutover/) ; pour Webflow, les redirections CMS ajoutent une couche de vérification à part entière.

![Itinéraire qui contourne une erreur 404 vers une page active](/assets/img/posts/2026-11-24-exporter-un-site-webflow-sans-perdre-les-redirections-de-vos-pages-cms/image-02-baec85cd8e19.webp)

## Installer les règles dans le bon ordre

Commencez par les lignes une-à-une à forte valeur : ancien article, page produit remplacée, page de campagne encore liée. Ensuite seulement, ajoutez une règle de dossier ou un motif plus large si vous avez vérifié qu’il ne capture pas une exception.

Prenons ce scénario :

- `/blog/guide-export-webflow` devient `/ressources/exporter-webflow/` ;
- `/blog/ancien-modele` n’a plus d’équivalent et va vers `/ressources/` ;
- `/blog/(.*)` peut, si votre plateforme le prend en charge, servir de filet de sécurité vers une destination documentée.

La première règle doit passer avant la troisième. Ne supposez pas que la syntaxe de capture de Webflow est celle de votre CDN : relevez-la dans la documentation de votre cible et testez-la en préproduction. Si vous migrez depuis Webflow, vous pouvez également [exporter les 301 en CSV](https://help.webflow.com/hc/en-us/articles/33961211526291-Import-export-301-redirects) comme sauvegarde de référence ; ce fichier décrit l’intention, mais ne configure pas automatiquement un autre hébergeur.

## Le test qui compte : regarder le premier saut

Sur une URL ancienne, le résultat acceptable n’est pas seulement « la page s’affiche ». Vérifiez :

1. que la réponse est bien une redirection permanente lorsque c’est votre choix ;
2. que le premier emplacement indiqué est l’URL finale, sans chaîne de détours ;
3. que la destination répond 200 et correspond au sujet promis ;
4. que les liens internes de la page chargée n’envoient pas vers l’ancien domaine ;
5. qu’un chemin inexistant affiche votre page 404 prévue.

Faites ce passage dans un navigateur privé et sur mobile pour limiter les illusions de cache. Après une bascule de domaine, contrôlez aussi la variante `www` ou non-`www`, HTTPS et les liens contenant des paramètres de campagne. La [checklist de fumée d’un export Framer](https://the-lean-ecommerce.github.io/2026/11/23/how-i-smoke-test-a-framer-static-export-before-i-publish-it/) est utile pour les assets et les interactions ; ajoutez-y votre registre de chemins pour ne pas séparer expérience de page et entrée dans le site.

![Checklist visuelle de validation après migration Webflow](/assets/img/posts/2026-11-24-exporter-un-site-webflow-sans-perdre-les-redirections-de-vos-pages-cms/image-03-4f3fbae06e8c.webp)

## Trois erreurs faciles à éviter

**Faire pointer toutes les anciennes pages vers l’accueil.** Cela masque le problème sans rendre service à la personne qui cherchait un article précis. Préférez une correspondance directe ou une catégorie réellement pertinente.

**Importer un gros motif avant les exceptions.** Une règle large peut absorber une page stratégique. Dans Webflow comme dans beaucoup d’outils de routage, l’ordre est une règle métier, pas un détail de mise en forme.

**Tester uniquement la nouvelle navigation.** Les visiteurs arrivant par un ancien résultat de recherche ne suivent pas votre menu. Testez les anciennes URLs dans le registre, une par une, puis surveillez les 404 après la mise en ligne.

## Votre prochaine action

Avant d’exporter, créez dix lignes de registre pour les chemins qui apportent réellement du trafic ou des liens. Exportez ensuite le site Webflow avec [ExFlow](https://exflow.site/webflow), déployez une préproduction et faites passer ces dix URLs avant de modifier le DNS. Une fois cette routine en place, vous pourrez appliquer le même principe à un [export Squarespace](https://exflow.site/squarespace) ou à un [site Framer](https://exflow.site/framer) sans confondre sauvegarde de fichiers et continuité des adresses.

En bref : une migration statique réussie ne transporte pas seulement des pages. Elle conserve aussi les chemins qui y mènent.
