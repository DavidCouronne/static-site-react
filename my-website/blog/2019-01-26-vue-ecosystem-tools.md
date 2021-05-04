---
author: David Couronné
date: 2019-01-26
post: true
title: Vue ecosystem Tools
description: Tools for Vue, Vuepress, Nuxt, Gridsome
tags:
  - gridsome
  - nuxt
  - vuepress
  - vue
image: ''
sidebar: auto
---

## Cli

### Vue CLI 3

[Vue CLI 3](https://cli.vuejs.org/)

```bash
npm install -g @vue/cli
```

Vue UI:

```bash
vue ui
```

Creating project:

```bash
vue create hello-world
```

Commands:

```bash
vue serve
vue build
```

### Gridsome

[Gridsome](https://gridsome.org/docs/)

```bash
npm install --global @gridsome/cli
```

```bash
gridsome create my-gridsome-site
```

Issue: if process stop at etape 3:

1. CTRL+C
2. `cd my-gridsome-site`
3. `yarn upgrade --latest`

```bash
gridsome develop
gridsome build
```

[Quick Start Guide](https://lobotuerto.com/blog/quickstart-guide-for-a-new-gridsome-project/)
[Building a Blog](https://alligator.io/vuejs/gridsome-list-posts/)

Issue with Python 3.x installed:

```bash
C:\Program Files\nodejs\node_modules\npm\bin\node-gyp-bin\\..\..\node_modules\node-gyp\bin\node-gyp.js" rebuild )  else (node
"" rebuild )
gyp info it worked if it ends with ok
gyp info using node-gyp@3.8.0
gyp info using node@11.8.0 | win32 | x64
gyp ERR! configure error
gyp ERR! stack Error: Command failed: C:\Program Files (x86)\Python37-32\python.EXE -c import sys; print "%s.%s.%s" % sys.version_info[:3];
gyp ERR! stack   File "<string>", line 1
gyp ERR! stack     import sys; print "%s.%s.%s" % sys.version_info[:3];
gyp ERR! stack                                ^
gyp ERR! stack SyntaxError: invalid syntax
gyp ERR! stack
gyp ERR! stack     at ChildProcess.exithandler (child_process.js:297:12)
gyp ERR! stack     at ChildProcess.emit (events.js:197:13)
gyp ERR! stack     at maybeClose (internal/child_process.js:978:16)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (internal/child_process.js:265:5)
gyp ERR! System Windows_NT 10.0.17763
gyp ERR! command "C:\\Program Files\\nodejs\\node.exe" "C:\\Program Files\\nodejs\\node_modules\\npm\\node_modules\\node-gyp\\bin\\node-gyp.js" "rebuild"
```

Solution

```bash
npm config set pytthon C:\Python27
```

### Vuepress

[Vuepress](https://vuepress.vuejs.org/)

```bash
npm install -g vuepress
```

### Nuxt.js

[Nuxt.js](https://nuxtjs.org/guide/installation)

```bash
npx create-nuxt-app <project-name>
```

## VSCode extensions

- Vetur
- Material Icon Theme

## Yarn and Lerna

- [Monorepo with Yan and Lerna](https://medium.com/trabe/monorepo-setup-with-lerna-and-yarn-workspaces-5d747d7c0e91)
