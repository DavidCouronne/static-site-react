---
author: David Couronné
date: 2019-11-20
post: true
title: 'Flutter: Installer Flutter sur Windows 10'
description: Comment installer Flutter sur Windows 10
tags: []
image: https://res.cloudinary.com/dpw19qolx/image/upload/q_auto,f_auto,g_auto,w_auto,dpr_auto/v1561739205/westboundary-photography-chris-gill-lBL7rSRaNGs-unsplash.jpg
---

# Etapes d'installation de Flutter

Cet article reprend la documentation officielle de Flutter: [https://flutter.dev/docs/get-started/install/windows](https://flutter.dev/docs/get-started/install/windows)

<!--truncate-->

## Télécharger les outils.

Nous allons commencer à télécharger tous les outils dont nous aurons besoin, mais sans les installer à cette étape:

- Nous avons besoin d'un éditeur de code. Nous allons prendre [Visual Studio Code](https://code.visualstudio.com/download)

- Pour fonctionner correctement, Flutter a besoin de [Git](https://git-scm.com/downloads). L

- Nous avons ensuite besoin d'[Android Studio](https://developer.android.com/studio). Cette installation va nous permettre d'obtenir les SDK pour le dévéloppement d'applications sur Android, et d'un émulateur de smartphone Android.

- Nous avons besoin de [HAXM](https://github.com/intel/haxm) pour l'accélération matérielle de l'émulateur Android.

- Optionnel: si vous voulez développer pour un Iphone, ou un Ipad, c'est possible, même sous Windows 10. La procédure sera détaillée plus tard, mais tant qu'à télécharger et installer des outils, vous pouvez au moins installer la version bureau de Itunes. Attention: il ne faut pas installer la version "Microsoft Store". Sur la page de téléchargement de [Itunes](https://www.apple.com/fr/itunes/), il faut un peu scroller vers le bas jusqu'à "vous cherchez d'autres versions ?", puis cliquer sur windows, et vous arrivez à "Téléchargez la dernière version pour Windows.".

- Ensuite il nous faut Flutter lui-même. Sur la page [Flutter](https://flutter.dev/docs/get-started/install/windows), scroller jusqu'à 'Get the Flutter SDK', puis télécharger.

## Commencer à installer

1. Visual Studio Code. L'installation ne pose pas de problème.
2. Git. Aucune difficulté non plus.
3. Activer l'HAXM... Décompresser le fichier zip, puis lancer l'installateur.
4. Android Studio. Il faut choisir "custom" pour pouvoir installer un émulateur Android.
5. Exécuter Android Studio ! Et oui, c'est au premier lancement que cette application va télécharger et installer les SDK dont nous avons besoin. Ca prend un certain temps (voire même un temps certain !)
6. Optionnel: si vous voulez faire tourner votre appli sur un Iphone, installer Itunes.
7. Flutter: ce n'est pas une installation à proprement parler. Il faut décompresser le fichier zip, puis placer tout le contenu dans un endroit futé, par exemple `C:\Workspace\flutter_src\`
