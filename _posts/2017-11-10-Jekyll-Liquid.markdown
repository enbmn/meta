---
layout: single
title: Liquid pour Jekyll
date: '2017-11-10'
excerpt: >-
  Liquid est un langage de templating en Ruby conçu à l'origine pour Shopify et
  désormais disponible comme projet open source sur Github.
share: true
toc: true
toc_label: Sommaire
toc_icon: file-text
tags:
  - outils
  - langage
permalink: 'carnet/:title'
author_profile: false
related: false
header:
  image: null
  overlay_color: 'rgb(0, 0, 0)'
---

Je ne vais pas ici vous apprendre à utiliser **Liquid** dans le détail (j'en suis bien incapable), l'idée est simplement de vous le faire connaître, et de vous dire en gros à quoi il sert car c'est une syntaxe nécessaire pour personnaliser les thèmes de [Jekyll]({{ site.baseurl }}/carnet/Jekyll).

# À quoi sert **Liquid** (dans **Jekyll**)

**Liquid** est donc un langage utilisé par **Jekyll** pour la création de ses _templates_.<br>
Pour rappel, **Jekyll** est un générateur de sites statiques (c'est à dire sans `PHP` et sans base de données, tout est en `HTML` pur). Il utilise une version dérivée de **Liquid**, plus légère que celle de shopify et bien documentée [ici](https://Jekyllrb.com/docs/templates/).

Un tel site pourra avoir une structure statique écrite **Liquid** dans un contenant `HTML`. Ce qui permettra, au moment de la compilation qui va générer toutes les pages du site, d'aller chercher divers éléments statiques pré-construits (dans _includes_) d'un projet et de les insérer dans nos modèles de pages (dans _layouts_) en les transformant en `HTML`.

En découpant ainsi les composants d'un site pour les réutiliser on facilite le déploiement, la maintenance et toutes les mises à jours que l'on souhaiterait y apporter (sur le principe de `XSLT` qui est le langage de _templating_ pour `XML`).

La syntaxe **Liquid** est simple et bien différenciée du `HTML` :

- les accolades et le signe pourcentage {% raw %}`{% %}` {% endraw %} pour les **tags**
- la double accolade {% raw %}`{{ }}` {% endraw %} pour les **objects**.<br>

Quand **Jekyll** génère votre site, sa première action est l'interprétation du code **Liquid** pour "fabriquer" la structure des pages `HTML`. Elles vont ensuite recevoir leur contenu, vos billets et pages en markdown, généré lui par un convertisseur ([Kramdown](https://kramdown.gettalong.org/index.html) le convertisseur **Markdown** vers `HTML` de **Jekyll**). Le tout est ensuite parsé dans le modèle généré juste avant et les pages `HTML` sont enregistrées dans la section `_site` de votre dépôt.

# De quoi est fait Liquid ?

Survol des trois principales composantes du langage.

## Les objets (objects)

Les objets **Liquid** sont définis par des doubles accolades {% raw %}`{{ }}`{% endraw %} dans lesquels on aura un objet et sa propriété {% raw %}`{{site.title}}` {% endraw %} ici l'`objet` site fait appel à la propriété `title`, ainsi dans **Jekyll** l'information, c'est à dire dans ce cas le nom du site, sera récupérée de l'objet site, ces informations sont contenues dans le fichier `.config.yml` en syntaxe [YAML](https://fr.wikipedia.org/wiki/YAML).

## Les tags (tag)

Les tags peuvent servir à des opérations logiques dans les _templates_

- résoudre des conditions<br>
  {% raw%}

```
{% if my_page.title %}
  {{ my_page.title }}
{% endif %}
```

{% endraw%}

- invoquer des templates<br>
  {% raw %}

```
<!DOCTYPE html>
<html>
<body>
  <header>
    {% include header.html %}
  </header>
</body>
</html>
```

{% endraw %}

- créer des boucles {% raw %}

```
{% for post in site.posts%}
  {% include post_block.html %}
{% endfor %}
```

{% endraw %}

Il y a quatre types de tags

- controle flow tag
- Iteration tags
- Theme tags
- Variable tags

## Les filtres (filters)

Deux éléments séparés par un pipe `|`, un paramètre à gauche du pipe, le filtre et éventuellement on peut encore passer des paramètres au filtre en utilisant les deux points `:`.

Les filtres sont utilisés sur objects ou des strings (entre `‘’`) et servent à formater les données en sortie.<br>
{% raw %}<br>
`{{ site.title | upcase }}`<br>
{% endraw %}<br>
donnera<br>
`LE TITRE DU SITE` en capitale<br>

Autre exemple avec un paramètre passé au filtre :<br>

Pour afficher la date d'une page,<br>
`{% raw %}{{ page.date | date: "%F" }}{% endraw %}`<br>
la sortie sera codée au format défini par le filtre, ici `| date: %F` et le rendu sera `AAAA-MM-JJ`.<br>
Pour les formats de date en `RUBY,` tout est [ici](http://www.strfti.me/).

Il y en a 8 sortes de filtres

- Array filters
- Color filters
- HTML filters
- Math filters
- Money filters
- String filters
- URL filters
- Additional filters

# Aller plus loin

Si vous avez besoin d'aller plus loin après ce survol du langage, rendez-vous sur [cette page](https://shopify.github.io/liquid/), l'essentiel s'y trouve avec pour chaque object, filtre ou tag, des explications et des exemples.

# Autres sources:

- [La page](https://help.shopify.com/themes/liquid) consacrée au _templating_ en pur **Liquid**
- [Une page](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) avec l'essentiel de la syntaxe
- [Un tutoriel](https://www.grafikart.fr/tutoriels/html-css/jekyll-505) d'installation de **Jekyll** en français ou il est question de **Liquid**
