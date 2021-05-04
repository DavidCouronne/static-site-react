---
title: 'Continuous Deployment with Vuepress, Travis CI and Firebase Hosting'
description: Déploiement continu d'un site avec Travis CI et hébergement chez Firebase
author: David Couronné
date: 2019-06-27
post: true
tags:
  - programming
---

<!--truncate-->

# Installer les outils de base

## Travis CI

Prérequis: avoir un compte Travis CI

Cette installation demande un peu de temps:

1. Installer Ruby: [Ruby](https://rubyinstaller.org/downloads/). Prendre l'installateur recommandé.
2. Vérifier l'installation:

```bash
ruby -v
```

3. Installer Travis CI

```bash
gem install travis -v 1.8.10 --no-rdoc --no-ri
```

4. Vérifier l'installation:

```bash
travis version
```

## Firebase CLI

Prérequis: avoir un compte Firebase !

```bash
npm install -g firebase-tools
```

Puis

```bash
firebase login
```
