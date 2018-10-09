---
layout: single
title: Un workflow nomade
date: '2018-04-01'
tags:
  - workflow
  - outils
permalink: 'carnet/:title'
excerpt: >-
  Un billet sur les outils mis en œuvre dans mon travail au quotidien, de prise
  de note, de traitement ou de rédaction, sur plusieurs machines.
toc: true
toc_label: Sommaire
toc_icon: file-text
share: true
author_profile: false
related: false
header:
  teaser: /assets/images/atomMD.png
  image: null
  overlay_color: 'rgb(0, 0, 0)'
---

Les derniers projets sur lesquels j'ai eu à travailler m'ont confirmé une chose. Il devient de plus en plus difficile de travailler de façon fluide, en équipe, voire même seul, dans le cadre contraint d'un service et avec des outils métiers.

# Définition des enjeux

- Je veux pouvoir travailler sur des machines différentes (PC, Linux et Mac à la BM ou chez moi), sur les mêmes fichiers, sans effets de bords (crash, perte de mise en pages). J'ai donc besoin d'un format ouvert et interopérable.

- Il me faut aussi avoir un accès décentralisé à mes fichiers de travail, avant de les finaliser pour les publier ou les archiver sur les serveurs Ville (saturés et lents), mais en garantir une sauvegarde intermédiaire, voire un versionning.

- Je veux aussi pouvoir partager mes fichiers pour un travail collaboratif. Et là ça se complique, surtout si j'ajoute que j'aimerai bien me passer du malheureusement l'incontournable **Google Drive**.

# Ébauches de réponses

Pour mon propre usage j'ai mis en place un _workflow_ très souple et relativement simple qui répond à tous mes besoins (ou presque).

## Les outils

Voici les briques de mon "système", il n'y a rien de révolutionnaire.

### Markdown

Je l'ai déjà écrit, [**Markdown**]({{ site.baseurl }}/carnet/utiliser-Markdown) est, pour le texte, la clef de voute de l'interopérabilité. Il se lit dans n'importe que logiciel, peut se transformer de multiples manières (grâce à [**Pandoc**](https://enacit1.epfl.ch/markdown-pandoc/#installation-de-pandoc) ou à des éditeurs **Markdown**) et offre une syntaxe suffisante pour 90 % des besoins rédactionnels

### LibeOffice

Installé ou en version portable (pour contrer _proxynator_), il vous permettra de travailler avec des tableurs (je proscris **Writer**, comme d'ailleurs et surtout **Word**). On peut aussi l'utiliser pour des tâches spécifiques en ligne de commande (conversion par lot essentiellement). En `XML` il permet de récupérer les fichiers dans **Oxygen** pour les traiter par des feuilles de style `XSLT`, pour travailler à plusieurs sur les index de noms de personnes en `TEI` par exemple. Il est, transposé en fichier `XML` beaucoup moins verbeux que son concurrent **Excel** (si on a une version récente).

### Git

Le logiciel [**Git**](https://fr.wikipedia.org/wiki/Git), créé par Linus Torvalds (créateur de **Linux**), implémenté dans [**Github**](https:www.github.com), [**GitLab**](https://about.gitlab.com/), [**FramaGit**](https://framagit.org/), [**BitBucket**](https://bitbucket.org/), etc. est un outil de _versionning_ extrêmement puissant destiné à l'origine aux développeurs. Mais il peut servir au stockage de notes, de textes, voire à l'hébergement de sites web (grâce à [**Jekyll**]({{ site.baseurl }}/carnet/Jekyll)), d'ailleurs ce site tourne depuis **Github**). Son grand avantage est bien entendu son système de versionning qui garde trace de tous les changements effectués sur un fichier. Son utilisation, au travers du `terminal` est par contre plus difficile à prendre en main.

### Dropbox

Pour l'accès distant à mes fichiers, j'utilise ce service, à défaut d'un autre pour le remplacer... Son client permet un accès depuis le _finder_ ou l'explorateur de fichiers, et surtout il offre la possibilité d'une synchronisation quasi immédiate, et le partage de fichiers.

### Atom

Pour éditer tout ça, j'utilise essentiellement [**Atom**](https://atom.io/), couteau suisse du développeur, grâce à une multitude de plugins, il permet l'édition de code, mais aussi de **Markdown**, avec coloration syntaxique et mode preview. Le plugin **Pandoc** permet des exports (on peut styler tout ça au besoin avec du `CSS`), mais il faut par contre avoir **LaTex** sur sa machine si l'on veut du `PDF`. **Atom** embarque aussi un client **Github** pour des `commit` directement depuis son interface, mais je préfère passer par le `terminal`.

### Ulysses

Pour qui ne travaille que sur du texte, [**Ulysses**](https://ulysses.app/) est très bon aussi, en outre il embarque des convertisseur vers `txt`, `HTML`, `PDF`, `Doc`, le tout déjà stylé. Il permet aussi la connexion à des services de cloud. Là ou il est très puissant, c'est dans sa façon de gérer les blocs de textes, on les édite simplement, le **Markdown** est natif, on peut ensuite les organiser entre-eux pour créer des chapitres, évitant ainsi d'avoir à la rédaction une page infinie. À noter que contrairement à **Atom**, il est payant.

### Etc.

Voilà pour l'essentiel, il y a d'autres outils, d'un usage parfois plus ponctuel, sur lesquels je reviendrai peut-être, et parfois aussi ce _workflow_ change... Car _in fine_ le maître mot reste la souplesse et l'interopérabilité.
