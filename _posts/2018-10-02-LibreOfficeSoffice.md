---
layout: single
title: Convertir en lot de XLS vers CSV en ligne de commande
date: '2018-10-02'
tags:
  - workflow
  - outils
  - Libreoffice
  - terminal
  - csv
permalink: 'carnet/:title'
excerpt: >-
  Comment convertir des fichiers xls vers csv, en masse, avec avec la librairie
  **soffice** de LibreOffice .
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

Convertir en lot des fichiers xls en `csv` peut s'avérer utile. On pourra en particulier préparer depuis des fichiers de catalogage ou de récolement produit sous excel, des csv bien encodés et propres au versement : en UTF-8, avec le séparateur `,`. [^1]

Dans la mesure du possible (_i.e_ dans un monde parfait), il est évident qu'on produira directement un `csv` bien formé (si toutefois on a **LibreOffice**, mais je rappelle qu'il existe en version [portable](https://fr.libreoffice.org/download/portable-versions/)), mais il peut être utile de travailler avec un fichier `xls` ou `odt`. En particulier si l'on a besoin de plusieurs feuilles pour préparer le travail de catalogage, ou de tri des données à verser.

> Par exemple on peut avoir besoin de cataloguer / récoler tout un lot de documents iconographiques en vue d'une numérisation, mais vouloir dédoublonner la liste avant le versement, ou mettre de coté des documents sous droits, etc.

Le `csv` produit avec la ligne de commande ne s'occupera que de la première feuille. Le fichier `xls` reste inchangé.

Pour ce faire **LibreOffice** offre dans sa libairie **soffice** des filtres à utiliser directement depuis le `terminal`, bien entendu on peut aussi écrire une macro, mais en cherchant une méthode de conversion par lot, je suis tombé sur celle-ci et elle est très rapide à utiliser.

# La commande

**LibreOffice** doit être fermé, dans le terminal, on passe au début de la commande le chemin vers `soffice` le filtre choisi (ici `--convert to csv :"Text - txt - csv (StarCalc)"`), ses options, enfin le chemin vers les `xls` et le chemin de sortie.

`/Applications/LibreOffice.app/Contents/MacOS/soffice --convert-to csv:"Text - txt - csv (StarCalc)":44,34,76,,,,,, /Users/.../*.xls --outdir /Users/...`

# Le filtre

Celui qui nous intéresse est le suivant :

- `Text - txt - csv (StarCalc)` : _Comma separated values_

# Les options du filtre

Les options à passer sont sibyllines, voir [ici](https://wiki.openoffice.org/wiki/Documentation/DevGuide/Spreadsheets/Filter_Options). Il y en a 9, elles consistent en un chiffre, séparé par des virgule, dans notre cas trois suffisent :

- `44` : code le séparateur `,`
- `34` : code le délimiteur de texte `""`
- `76` : code l'encodage `UTF-8`

# Bonus

Mais **Soffice** permet de faire d'autres conversions bien pratiques.

## Convertir en `PDF`

Avec ce filtre, on peut opérer la conversion en lot de documents `odt` ou `doc(x)` vers le format `PDF` :

- `--convert-to pdf:writer_pdf_Export`
- `/Applications/LibreOffice.app/Contents/MacOS/soffice --convert-to pdf:writer_pdf_Export /Users/...*.odt --outdir /Users/...`

## Convertir en `TXT`

Tout aussi utile la conversion d'un `.doc`, `.docx`, ou `.odt` vers `txt` pour obtenir une version débarrassée de tout balisage incongru (attention, les liens sautent aussi) :

- `--convert-to "txt:Text (encoded):UTF8" *.doc ou odt`
- `/Applications/LibreOffice.app/Contents/MacOS/soffice--convert-to "txt:Text (encoded):UTF8" *.doc ou odt --outdir /Users/...`

À vous de jouer.

--------------------------------------------------------------------------------

[^1]:Pour mémoire, **Excel** à tendance à utiliser le `;` – incompatible avec les outils de chargement des bases de données ou les plugins de chargement en masse de bibliothèque numériques comme celui d'**Omeka** par exemple.
