---
title: Vuepress et PWA
description: Configurer Vuepress comme Progressive Web App
date: 2019-06-26
---

## Configurer Vuepress en PWA

PWA: Progressive Web App

Cela permet de rendre notre site disponible hors connexion.

Nous allons commencer par générer les icones et le manifeste.

## Générer le manifeste

Déjà, il nous faut une image (ou icone) pour l'installation. Là c'est un peu comme vous voulez:

- Paint c'est pas mal
- Pour ma part j'ai utilisé [editor.method.ac](https://editor.method.ac/). Très basique..

Ensuite, il nous faut convertir cette image (ou icone) en plein de formats différents.

Convertisseur d'images en icones d'installation: [FaviconConverter](https://favicon.io/favicon-converter/)

Ce site permet en plus d'avoir un fichier manifeste qu'il ne reste plus qu'à configurer un peu !

```json
{
  "name": "Mon super site de documentation sur mon super projet",
  "short_name": "Projet",
  "theme_color": "#2196f3",
  "background_color": "#2196f3",
  "display": "fullscreen",
  "start_url": "/index.html",
  "icons": [
    {
      "src": "images/icons/android-chrome-192x192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "images/icons/android-chrome-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
```

Nous allons voir que faire de tous ces fichiers !

## Configurer Vuepress

### Installer le plugin PWA

Il faut d'abord installer le plugin @vuepress/plugin-pwa

```bash
yarn add  @vuepress/plugin-pwa -D
```

### Installer le manifeste et les icones

Les fichiers `manifest.json` et `favicon.ico` sont à placer dans le dossier `.vuepress/public/`

Ensuite il faut créer un dossier `.vuepress/public/images/icons` dans lequel vous allez mettre les différentes icones générées.

:::warning Attention
Tout ce qui est dans le dossier `public` se retrouve à la racine. Donc les chemins sont bien `images/icons/`
:::

### Paraméter vuepress

Dans le fichier `config.js` du dossier `.vuepress`:

```js
module.exports = {
  head: [
    ['link', { rel: 'manifest', href: '/manifest.json' }],
    ['link', { rel: 'icon', href: '/favicon.ico' }],
  ],

  plugins: [
    [
      '@vuepress/pwa',
      {
        serviceWorker: true,
        updatePopup: true,
      },
    ],
    ['sitemap', { hostname: 'https://www.monsite.fr/' }],
  ],
}
```

### Tester

Déployer le site, puis l'ouvrir avec Google Chrome. Normalement, il devrait être possible de l'installer !
