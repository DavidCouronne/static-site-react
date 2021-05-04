---
title: Démarrer en HTML Partie 3 🎉
date: 2019-05-25
author: [davidcouronne]
tags: ['HTML', 'CSS', 'Tutoriel']
canonical_url: false
description: 'Ajouter un peu de CSS'
cover: ./covers/koala.jpg
---

> _Prérequis_ : Avoir lu la [partie 2](/demarrer-en-html-partie-2)

L'objectif de cette partie n'est pas de faire un cours sur le CSS mais juste d'en voir quelques principes et fonctionnalités de base.

Le CSS(Cascading Style Sheets) permet d'appliquer des styles, comme des couleurs, des polices de caractères, des bordures, etc... à notre contenu HTML.

Il va "agir" soit sur des balises _sémantiques_ , soit, et là ça se complique, sur des balises _non sémantiques_.

## Un exemple simple

Reprenons notre site. Si par exemple nous voulons que notre `header` soit écrit en rouge, nous allons écrire une "propriété" CSS qui va ressembler à:

```css
header {
  color: red;
}
```

Deux approches sont possibles:

1. Soit intégrer le CSS au fichier HTML.
2. Soit mettre le CSS dans un fichier séparé.

### Intégrer le CSS dans le fichier HTML

Cette approche très simple permet de faire quelques tests, mais n'est pas du tout utilisée en production en général. Il y a bien sûr des exceptions, mais cela sort du cadre de ce tutoriel.

Néanmoins, je vais vous montrer comment faire avec notre fichier d'exemple:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Notre première page Web</title>
    <style>
      header {
        color: red;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Le monde de Gerflor</h1>
    </header>
    <nav>
      <ul>
        <li>Accueil</li>
        <li><a href="contact/index.html">Contact</a></li>
      </ul>
    </nav>
    <main>
      <p>Mon voyage dans la Beauce</p>
      <p>Le meilleur camping du Havre</p>
      <p>
        Une photo d'un chat rigolo
        <img
          src="https://res.cloudinary.com/dpw19qolx/image/upload/v1549194479/samples/animals/kitten-playing.gif"
          alt="chat rigolo"
        />
      </p>
      <p>La vie des cailloux en milieu aquatique</p>
      <img src="./img/image1.jpg" alt="Une image" />
    </main>
    <footer>
      <p>Image1 - Quelle belle image !</p>
      <img src="./img/image1.jpg" alt="" />
      <p>Image2 - Bof...</p>
    </footer>
  </body>
</html>
```

Comme vous pouvez le voir, le CSS est compris dans les balises `<head></head>` et est entouré des balises `<style></style>`

### Lien vers un fichier CSS externe

La commande va ressembler à:

```html
<head>
  <link rel="stylesheet" href="theme.css" />
</head>
```

Nous allons créer à la racine de notre dossier un fichier `theme.css`, dans lequel nous allons mettre le style:

![vs css](./images/vscode-css.gif)

```css
header {
  color: red;
  background-color: rgb(233, 233, 155);
}
```

Puis nous allons lier ce fichier à notre fichier `index.html`:

```html
...
<head>
  <meta charset="UTF-8" />
  <title>Notre première page Web</title>
  <link rel="stylesheet" href="theme.css" />
</head>
...
```
