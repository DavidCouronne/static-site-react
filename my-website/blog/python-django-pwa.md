---
author: David Couronné
date: 2019-07-02
post: true
title: Python Django PWA
description: Comment créer une PWA avec Django
tags:
  - pwa
  - django
  - python
image: https://res.cloudinary.com/dpw19qolx/image/upload/q_auto,f_auto,g_auto,w_auto,dpr_auto/v1561883470/greg-rakozy-oMpAz-DN-9I-unsplash.jpg
---

<!--truncate-->

## Installer les outils

1. [Python](https://www.python.org/downloads/)
2. [Django](https://www.djangoproject.com/):

```bash
pip install Django
```

## Créer un nouveau projet

Nous allons créer un nouveau projet: `djangopwa`

Pour cela, dans un dossier bien choisi, ouvrez le terminal puis:

```bash
django-admin startproject djangopwa
```

Entrez dans le dossier `djangopwa`:

```bash
cd djangopwa
```

Puis créez une nouvelle application `posts`:

```bash
django-admin startapp posts
```

Il est temps d'ouvrir le dossier avec Visual Studio Code !

```bash
code .
```

Créez un dossier `templates` à l'intérieur du dossier `posts`. Puis créez à l'intérieur du dossier `templates` un nouveau dossier `posts`. Vous devez avoir un répertoire comme ça:

`djangopwa/posts/templates/posts`

A l'intérieur de ce repertoire vous allez créer deux fichiers: `index.html`et `base.html`.

Pour résumer vous devez avoir une arborescence comme ça:

![Directory](https://cdn-images-1.medium.com/max/1200/1*vYSh7nrw97QKre6DtV6iqA.png)

Il est temps d'écrire un peu de HTML ! Commençons par la mise en page du site, dans le fichier `base.html`:

```html
<!DOCTYPE html>
<html>
  {% load static %}
  <head>
    <title>Feeds</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta charset="utf-8" />
    <script
      src="https://code.jquery.com/jquery-3.2.1.slim.min.js"
      integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN"
      crossorigin="anonymous"
    ></script>
    <script
      src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js"
      integrity="sha384-ApNbgh9B+Y1QKtv3Rn7W3mgPxhU9K/ScQsAP7hUibX39j7fakFPskvXusvfa0b4Q"
      crossorigin="anonymous"
    ></script>
    <script
      src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta.3/js/bootstrap.min.js"
      integrity="sha384-a5N7Y/aK3qNeh15eJKGWxsqtnX/wWdSZSKp+81YjTmS15nvnvxKHuzaWwXHDli+4"
      crossorigin="anonymous"
    ></script>
    <link
      rel="stylesheet"
      href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta.3/css/bootstrap.min.css"
      integrity="sha384-Zug+QiDoJOrZ5t4lssLdxGhVrurbmBWopoEl+M6BdEfwnCJZtKxi1KgxUyJq13dy"
      crossorigin="anonymous"
    />
    <style type="text/css">
      .dropdown-span {
        text-align: center;
        color: white;
        background-color: #5bc0de;
      }
      span {
        color: white;
      }
      .footer {
        text-align: center;
        position: absolute;
        padding: 10px;
        color: white;
        width: 100%;
        bottom: 0;
      }
      .alink {
        text-decoration: none;
        color: white;
      }
      .alink:hover {
        text-decoration: none;
        color: white;
      }
      #content {
        padding-bottom: 5%;
      }
      html,
      body {
        margin: 0;
        padding: 0;
        height: 100%;
      }
      .wrapper {
        position: relative;
        min-height: 100%;
      }
    </style>
  </head>
  <body>
    <div class="wrapper">
      <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <a class="navbar-brand" href="#"><h2>Feeds</h2></a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav mr-auto">
            <li class="nav-item active">
              <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item active">
              <a class="nav-link" href="#">About us</a>
            </li>
          </ul>
        </div>
      </nav>
      <div id="content" class="container">
        <br /><br /><br />
        {% block content %} {% endblock %}
      </div>
      <div class="footer bg-dark">
        <p>&copy Feeds 2019</p>
        <a class="alink" href="#">Privacy policy</a>&nbsp
        <a class="alink" href="#">Contact us</a>
      </div>
    </div>
  </body>
</html>
```

Puis dans `index.html`:

```html
{% extends 'posts/base.html' %} {% block content %} {% load static %} <br /><br /><br />
<div class="feeds">
  {% for result in results %}
  <h3>{{result.title}}</h3>
  <br />
  Name:{{result.author}}
  <br />
  <p id="{{result.id}}">{{result.body}}</p>
  <hr />
  {% endfor %}
</div>
{% endblock %}
```

## Ajouter les fonctionnalités

Dans le dossier `djangopwa/posts/` il y a un fichier `views.py`où nous allons mettre:

```python
from django.shortcuts import render
from django.core import serializers
from . models import feed
import json
# Create your views here.
def index(request):
	template='posts/index.html'
	results=feed.objects.all()
	context={
		'results':results,
	}
	return render(request,template,context)

def base_layout(request):
	template='posts/base.html'
	return render(request,template)
```

:::tip Information
La fonction `index()` est chargée de servir la page d'accueil du site Web lorsque l'utilisateur est en ligne. Les résultats récupèrent tous les flux et sont envoyés au client en utilisant `context` `dict`. La fonction `base_layout ()` est utilisée pour rendre `base.html` qui sera mis en cache ultérieurement par le `service worker` pour la prise en charge hors ligne (nous en verrons plus à ce sujet plus tard).
:::

Dans le fichier `models.py`:

```python
from django.db import models

# Create your models here.
class feed(models.Model):
	id=models.IntegerField(primary_key=True)
	author=models.CharField(max_length=50)
	title=models.CharField(max_length=100)
	body=models.TextField()
```
