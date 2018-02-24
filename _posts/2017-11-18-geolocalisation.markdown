---
layout: single
title: Géolocaliser et faire des cartes
date: '2017-11-18 09:36:58 +0100'
excerpt: >-
  Parmi les enjeux de la mise en ligne de collections numérisées en
  bibliothèques, la question des modes d'accès aux documents demeure
  primordiale.
share: true
toc: true
toc_label: Sommaire
toc_icon: file-text
tags:
  - outils
  - géolocalisation
  - cartographie
permalink: 'carnet/:title'
author_profile: false
related: false
header:
  image: null
  overlay_color: 'rgb(0, 0, 0)'
---

Elle rejoint la problématique du nécessaire enrichissement des données mises à disposition dans une bibliothèque numérique.

Ainsi, pour des documents iconographiques tels que les cartes postales ou les dessins (paysages ou bâtiments), l'usager attend des informations de localisation précises, c'est pour lui un critère de recherche privilégié – en recherche avancée ou en facette. Pour cet usage, le champs `dc:coverage` joue ce rôle. Mais la recherche par le moteur n'est pas [ne doit pas être] le seul mode d'entrée dans une collection. Parlons de la géolocalisation, de la cartographie et de leurs mises en œuvre.

# Pourquoi

Inutile de s'étendre sur l'intérêt que présente pour une bibliothèque numérique la géolocalisation des documents numériques "figurants" des lieux : bâtiments, paysages, villes etc.<br>
Certaines plateformes géolocalisent les documents – c'est à dire les positionnent sur une carte – mais seulement au niveau des notices détaillées. C'est bien, mais assez peu pertinent et d'un intérêt limité pour l'usager arrivé à cette étape de la consultation.<br>
Il est à mon sens beaucoup plus pertinent d'utiliser la géolocalisation pour cartographier plusieurs documents. La carte devient ainsi un point d'entrée dans la collection, une interface graphique, un moyen d'accès direct aux contenus. Il est beaucoup plus utile à un usager de voir directement sur une carte quels sont les documents qui représentent un lieu, que d'avoir une carte situant le document dans sa notice détaillées (encore une fois, une fois arrivé là, l'image est inutile, le [`dc:coverage`](http://dublincore.org/documents/dcmi-terms/#éléments-coverage) suffit).

La cartographie devient dès lors un outil de datavisualisation. Pour certains contenus, c'est un moyen d'accès bien plus simple et direct que le moteur de recherche : on peut proposer dès la page d'accueil de "voir" la collection des cartes postales par leur localisation (bien plus simple que : on a des cartes postales, peut-être de la ville qui vous intéresse, mais d'abord allez dans le moteur de recherche, recherchez votre ville, dans le bon champ, parcourez la liste, et enfin allez voir le document... un peu long non ?). C'est aussi un moyen bien plus efficace qu'une liste pour donner à voir la "masse" des documents . Enfin des pastilles sur une carte font parfois sens en elles-mêmes et véhiculent de l'information, par exemple les pastilles qui géolocalisent les cartes postales des destructions durant la Grande Guerre suffisent pour "dessiner" la ligne de front, et montrer la "profondeur" de l'impact des combats sur le territoire et les populations civiles, etc.

Mais la mise en œuvre de la géolocalisation d'un corpus de plusieurs milliers de documents peut paraître insurmontable.

# Géolocaliser

Il y a plusieurs méthodes de géolocalisation, en fonction du corpus et des besoins, il convient d'adapter son approche et ses outils.

## De façon ponctuelle, manuellement

Souvent les données des documents numérisés sont issues du catalogue. Dans ce cas, on dispose comme base, si le catalogage est bien fait, d'informations de lieu dans les champs d'indexation. Si le catalogage est réalisé "pour" la numérisation, il faudra intégrer cet élément en veillant à ce que soit respecté la norme mise en œuvre (`dc:coverage` en rameau par exemple).<br>
Géolocaliser "à la main" dans un catalogue de bibliothèque n'est pas "pertinent" car beaucoup trop lourd (et pas exploité). Mais si cela doit être fait ponctuellement, au niveau de la bibliothèque numérique, il existe beaucoup d'outils pour récupérer les coordonnées cartographiques, je n'en cite qu'un très pratique selon moi pour les positionnements fins (par exemple bâtiments détruits, etc) c'est [Geojson](http://geojson.io/#map=2/20.0/0.0)[^1]. Cet outil vous permettra de positionner à la main des points et d'en récupérer les coordonnées sous forme de fichier `Json` (ou par simple copier coller).

<figure>
  <a href="{{ site.baseurl }}/assets/images/geojson.png">
  <img src="{{ site.baseurl }}/assets/images/geojson.png">
</a>
  <figcaption>L'interface de Geojson à gauche la carte, à droite la zone dynamique où le code se génère.</figcaption>
</figure>

## Géolocaliser en masse

C'est évidemment la meilleur façon de procéder. Voici quelques exemples d'outils utilisables pour géolocaliser en masse vos données (la fiabilité reste aléatoire) :

- **[Adresse data gouv](https://adresse.data.gouv.fr/`CSV`/)**. Pour géolocaliser des documents il suffit d'_uplaoder_ un fichier `CSV` contenant des données de type nom de rue ou de lieux. J'ai testé avec du rameau, cela fonctionne bien si il n'y a qu'une entée, l'outil vous propose ensuite de télécharger le fichier enrichi des longitudes, latitudes et de plusieurs autres colonnes qui pourront parfois être utiles (nom du lieu en langage naturel, code postal, région) ou servir à corriger des erreurs comme le score de reconnaissance.

<figure>
  <a href="{{ site.baseurl }}/assets/images/adresseGouv.png">
  <img src="{{ site.baseurl }}/assets/images/adresseGouv.png">
</a>
  <figcaption>L'interface de adresse.data.gouv.</figcaption>
</figure>

- sur le même principe existe [BatchGeo](https://fr.batchgeo.com) mais je ne l'ai pas testé, je me contente donc de le citer ici (si vous l'utilisez vous pouvez me faire des retours par mail) ;

- enfin un autre outil existe, mais qui fera l'objet d'un billet ultérieur, car c'est un autre type d'outil, non dédié à la géolocalisation et très puissant. Il s'agit de **[Dataiku](https://www.dataiku.com/)** logiciel de _data mining_ qui propose – entre autres – une fonction de géolocalisation basée sur le contenu textuel des colonnes de votre `CSV.` Il est aussi utile pour nettoyer les `CSV,` par exemple un fichier généré avec **adresse.data.gouv** contiendra des erreurs qu'il pourrait être laborieux de corriger ligne à ligne, c'est là que **Dataiku** [^2] entre en jeu. Mais je n'entre pas dans les détails ici.

# Cartographier

## En ligne

Pour des cartes publiables en ligne, de nombreux services web existent :

- [Open Street Maps](https://www.openstreetmap.org/), l'outil de cartographie collaborative, propose avec [Umap](https://umap.openstreetmap.fr) un outil intéressant. Les cartes peuvent être créées en important un `CSV` contenant les données de géolocalisation. Avec l'avantage d'être un outil open source basé sur une large communauté ;

<figure>
  <a href="{{ site.baseurl }}/assets/images/umaps.png">
  <img src="{{ site.baseurl }}/assets/images/umaps.png">
</a>
  <figcaption>Les communes de Meurthe-et-Moselle pour lesquelles existe une monographie géolocalisées avec Umap.</figcaption>
</figure>

- [Carto](https://carto.com/), un outil en ligne, mais service web propriétaire (avec toutefois un mode gratuit) ;
- **Google maps** propose aussi ce type de service, avec les mêmes réserves que le précédent.

## Dans votre bibliothèque numérique

Les outils les plus intéressants seront évidemment ceux embarqués dans votre bibliothèque numérique. Pour ce faire, il faudra demander à votre prestataire d'implémenter un outil qui pourra tirer parti des enrichissements de vos données (voire vous aider à les enrichir, en embarquant un module de géolocalisation par exemple). Il existe là encore beaucoup d'outils, souvent open source, qui permettent de réaliser des cartes.<br>
Je ne citerai que [Leaflet](http://leafletjs.com/), car je l'ai déjà [utilisé](http://journaldedurival.fr/html/cartographie.html) et sa documentation est très complète. **Leaflet** est une bibliothèque Javascript (basée sur **Open Street Maps**, mais qui peut embarquer des fonds de cartes issus de services web différents). **Leaflet** est relativement simple à implémenter dans une page web statique, sans devoir maîtriser `Javascript.`

À vous de tester ce qui conviendra le mieux à votre projet.

--------------------------------------------------------------------------------

[^1]: Il existe aussi le moteur de OSM, [Nominatim](https://nominatim.openstreetmap.org/) si on reste au niveau bâtiment public, monument, rue, ville ou village il proposera toujours les mêmes coordonnées.

[^2]: Voir aussi **[OpenRefine](http://openrefine.org/)**, développé par Google et open source.
