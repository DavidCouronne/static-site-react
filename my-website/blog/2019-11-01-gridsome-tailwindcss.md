---
title: 'Gridsome et Tailwind CSS sans plugin !'
date: 2019-11-01
published: true
author: davidcouronne
category: dev
tags: [Gridsome, TailwindCSS]
canonical_url: false
description: 'Installer Tailwind CSS avec Gridsome sans utiliser de plugin.'
cover_image: https://res.cloudinary.com/dpw19qolx/image/upload/t_cover-image/v1561523334/St_Michael_27s_Mount_II5302_x_2982.jpg
---

Dans cet article, nous allons juste aborder l'installation et la configuration de tailwindcss dans un projet Gridsome.

<!--truncate-->

## Installation de tailwindcss et de purgecss

```bash{codeTitle: "shell"}
yarn add tailwindcss @fullhuman/postcss-purgecss -D
```

Puis ajouter le fichier de configuration:

```bash{codeTitle: "shell"}
npx tailwind init
```

Ce qui doit donner le fichier suivant:

```javascript{codeTitle: "tailwind.config.js"}
module.exports = {
  theme: {},
  variants: {},
  plugins: []
}
```

## Importer tailwindcss

Le mieux est de créer un dossier `style`dans `./src/assets/` puis de créer un fichier `index.css`

```css{codeTitle: "./src/assets/index.css"}
@tailwind base;

@tailwind components;

@tailwind utilities;
```

Maintenant il faut importer tout ça dans le fichier `main.js`

```js{codeTitle: "./src/main.js"}
import "./styles/";
```

## Configurer purgecss

A la racine du projet, créer un fichier `purgecss.config.js`

```js{codeTitle: "purgecss.config.js"}
class TailwindExtractor {
  static extract(content) {
    return content.match(/[A-z0-9-:\\/]+/g)
  }
}

module.exports = {
  content: [
    './src/**/*.vue',
    './src/**/*.js',
    './src/**/*.jsx',
    './src/**/*.html',
    './src/**/*.pug',
    './src/**/*.md',
    './docs/**/*.md',
    './blog/**/*.md',
  ],
  whitelist: [
    'body',
    'html',
    'img',
    'a',
    'g-image',
    'g-image--lazy',
    'g-image--loaded',
    'active',
  ],
  extractors: [
    {
      extractor: TailwindExtractor,
      extensions: ['vue', 'js', 'jsx', 'md', 'html', 'pug'],
    },
  ],
}
```

Ensuite, au début du fichier `gridsome.config.js` , ajouter:

```js{1-8}{codeTitle: "gridsome.config.js"}
const tailwind = require('tailwindcss')
const purgecss = require('@fullhuman/postcss-purgecss')

const postcssPlugins = [
  tailwind(),
]

if (process.env.NODE_ENV === 'production') postcssPlugins.push(purgecss())


module.exports = {
  ...
```

Puis à la fin de ce même fichier:

```js{3-9}{codeTitle: "gridsome.config.js"}
module.exports = {
  ...
  css: {
    loaderOptions: {
      postcss: {
        plugins: postcssPlugins,
      },
    },
  },
}
```

Enjoy !
