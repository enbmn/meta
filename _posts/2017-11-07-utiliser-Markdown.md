---
layout: single
title: Utiliser Markdown
date: '2017-11-07 12:45:40 +0100'
tags:
  - outils
  - langage
permalink: 'carnet/:title'
share: true
toc: true
toc_label: Sommaire
toc_icon: file-text
excerpt: 'Qu''est-ce que la syntaxe Markdown, comment et pourquoi l''utiliser ?'
author_profile: false
header:
  image: null
  overlay_color: 'rgb(0, 0, 0)'
---

Voici ce qu'en dit Wikipedia :

> Markdown est un langage de balisage léger créé par John Gruber en 2004\. Son but est d'offrir une syntaxe facile à lire et à écrire. Un document balisé par Markdown peut être lu en l'état sans donner l'impression d'avoir été balisé ou formaté par des instructions particulières. [source](https://fr.wikipedia.org/wiki/Markdown)

# Portabilité, interopérabilité et pérennité

Tout ça à la fois ! Pouvoir prendre des notes partout avec n'importe quel outil et sur n'importe quelle plateforme (même un ipad ou un téléphone) et être sûr qu'elles resteront lisibles quelle que soit la plateforme ou le logiciel utilisé.

Ça n'a l'air de rien dit comme ça, mais qui, surtout si comme moi vous êtes dans un service doté de l'antépénultième version de **Word**, n'a pas été sollicité pour "aider" à ouvrir un fichier en `.odt` envoyé par un (relativement heureux) correspondant utilisant **LibreOffice**...

Pour paraphraser Wikipedia, **Markdown** est une syntaxe de balisage simple, au format texte, lisible par l'humain (c'est un peu moche mais n'est-ce pas le contenu qui compte ?) comme par les machines, ce qui le rend indépendant de tout logiciel spécifique (sauf pour le rendu, on y viendra). Un simple **WordPad** ou **TextEdit** suffisent pour rédiger et lire un texte en **Markdown** (il suffit d'utiliser l'extension `.md` ou `.markdown`).

Je ne vais pas vous faire ici un cours sur la syntaxe **Markdown**, [on trouve ça partout](https://www.google.fr/search?q=syntaxe+markdown&oq=syntaxe+markdown&aqs=chrome..69i57.3984j0j4&sourceid=chrome&ie=UTF-8), mais vous le verrez c'est extrêmement simple.

# Un format pour la diffusion multicanal

Le grand intérêt de **Markdown** est qu'il permet de produire "assez" simplement des documents sous différentes formes, pour différentes plateformes, moyennant un processeur. Processeur aujourd'hui embarqué dans la plupart des éditeurs **Markdown** (ou, moins pratique, disponible en ligne de commande avec [**Pandoc**](https://enacit1.epfl.ch/markdown-pandoc/#installation-de-pandoc)).

Et si je vous parle ici de **Markdown** c'est aussi parce que c'est l'outil de rédaction privilégié pour **Jekyll**.

Étant un langage à balise, il est aisément convertible en `HTML,` ce qui le rend très intéressant pour la rédaction de billets de blog. D'ailleurs on peut y insérer du balisage `HTML,` et des caractères spéciaux en code ISO, On dispose donc de tout ce qu'il faut pour écrire. Mais un même texte peut aussi être transformé en `PDF` depuis certains éditeurs (ou avec [**Pandoc**](https://enacit1.epfl.ch/markdown-pandoc/#installation-de-pandoc)) [^1], en`.odt` stylé (et oui...) etc.

Car **Markdown** dispose des fonctions de base de formatage d'un texte (l'équivalent de ce qu'il est possible de faire en `HTML`), en réalité suffisamment pour rendre un texte intelligible sans le surcharger. Un autre avantage est donc qu'il permet de rester concentré sur le texte, sur l'écriture, de le faire sans "trop" de distractions (quelle police choisir, quel style...).

# Les limites

Les limites à l'utilisation de ce format -- une fois passé le blocage psychologique "c'est un truc compliqué de geek" ! -- sont surtout des limites d'usage.

Évidemment si votre quotidien est la rédaction de lettres à en-têtes, **Markdown** ne sera pas adapté. Mais pour ce qui va de la prise de notes en réunion avec une tablette ou votre téléphone à la rédaction de billets de blog ou de comptes-rendus, c'est l'outil idéal.<br>
En effet, il permet d'écrire et de structurer rapidement et simplement vos notes, vous pouvez y revenir ensuite dans un autre outil, les amender et/ou les envoyer pour publication à votre responsable éditorial qui sera ravi de pouvoir copier-coller votre texte dans **Wordpress** sans à avoir à tout restyler (il y a une option dans **Wordpress** pour le **Markdown**).

<figure>
  <a href="{{ site.baseurl }}/assets/images/atomMd.png">
  <img src="{{ site.baseurl }}/assets/images/atomMd.png">
</a>
  <figcaption>Un texte en Markdown et sa prévisualisation dans Atom.</figcaption>
</figure>

Non il n'est pas à première vue _user friendly_, conditionnés que nous sommes par le dogme du **wysiwyg** (_what you see is what you get_, ce qui en passant n'est vrai qu'en apparence...). Mais en contrepartie il offre de multiples avantages.

# Des outils pour Markdown

Voici une petite sélection d'outils pour vous lancer dans **Markdown**.

## Écrire en Markdown :

### À installer

- [Atom](https://atom.io/) éditeur de texte libre et survitaminé, supporte Markdown et une multitude d'autres langages (fonctionne avec des plugins) ;
- [SimpleNote](https://simplenote.com/), pour **Ipad** et **Iphone** ;
- [nVALT](http://brettterpstra.com/projects/nvalt/) pour **Mac** ;
- [MarkdownPad](http://markdownpad.com/faq.html#portable) pour **Windows** qui à l'avantage d'être en version portable (si on ne peut pas installer sur sa machine ;)) ;
- [Remarkable](http://remarkableapp.net/) pour **Linux** à l'air pas mal (non testé).

### En ligne

- [StackEdit](https://stackedit.io/), extension **Google docs** pour **Markdown** et éditeur en ligne avec interface de saisie et quelques exports possibles (et gestion de **Google Drive** et **Dropbox**) ;

## D'autres outils pratiques

- [Tester Markdown en ligne avant de vous lancer](https://michelf.ca/projets/php-markdown/banc-d'essai/) ;
- [Heck yes markdown](http://heckyesmarkdown.com/) est une `API` en ligne qui vous permet de transformer une page web (html) en texte balisé en **Markdown** ;
- [Pandoc](http://pandoc.org/), le site officiel.

--------------------------------------------------------------------------------

[^1]: Toujours en ligne de commande mais il faut avoir en plus [LaTeX](https://fr.wikipedia.org/wiki/LaTeX) d'installé sur la machine.
