# NodeJS

Créé par [Ryan Dahl](https://en.wikipedia.org/wiki/Ryan_Dahl) en 2009.
C'est un environnement d'éxecution Javascript multi-plateforme, permettant d'exécuter du javascript en dehors d'un contexte navigateur
(par exemple: en mode serveur...).

## Determiner le type de gestion de module
[https://nodejs.org/api/packages.html#introduction](https://nodejs.org/api/packages.html#introduction)

Dans le fichier `package.json`:
```json
// package.json
{
  "type": "module" // commonjs
} 
``` 

### CommonJS
```js
const fs = require('fs');
```

### ES Modules
```js
import fs from 'node';
```

## Export

### CommonJS
`calculatrice.cjs` : 
```js
exports.add = function(a, b) {
    return a + b;
}

exports.sub = function(a, b) {
    return a - b;
}

exports.mul = function(a, b) {
    return a * b;
}

exports.div = function(a, b) {
    return b != 0 ? a / b : undefined;
}

// ------------------------------------

function add(a, b) {
    return a + b;
}

function sub(a, b) {
    return a - b;
}

function mul(a, b) {
    return a * b;
}

function div(a, b) {
    return b != 0 ? a / b : undefined;
}

module.exports = {
    add,
    sub,
    mul,
    div
}
```

`app.cjs`

```js
// import module
const calculatrice = require('./calculatrice.cjs');

calculatrice.add(a, b);
calculatrice.sub(a, b);
calculatrice.mul(a, b);
calculatrice.div(a, b);
```

### ES Modules
`calculatrice.cjs` : 
```js
export function add(a, b) {
    return a + b;
}

export function sub(a, b) {
    return a - b;
}

export function mul(a, b) {
    return a * b;
}

export function div(a, b) {
    return b != 0 ? a / b : undefined;
}

// ------------------------------------

function add(a, b) {
    return a + b;
}

function sub(a, b) {
    return a - b;
}

function mul(a, b) {
    return a * b;
}

function div(a, b) {
    return b != 0 ? a / b : undefined;
}

export {
    add,
    sub,
    div,
    mul
}
```

`app.cjs`

```js
// import module
import * as calculatrice from './calculatrice.mjs';
import { add, sub, mul, div } from './calculatrice.mjs';

calculatrice.add(a, b);
calculatrice.sub(a, b);
calculatrice.mul(a, b);
calculatrice.div(a, b);
```

## Créer un nouveau projet

1 - Lancer npm init qui va poser un ensemble de question afin d'initialiser le projet NodeJS. Un fichier `package.json` sera créé à la fin.

```bash
npm init

package name: (tp2)
version: (1.0.0) 0.0.1
description: Projet TP 2
entry point: (index.js) app.js
test command:
git repository:
keywords: tp node js
author: Thomas CILES
license: (ISC)
```

Résultat :
```json
// package.json
{
  "name": "tp2",
  "version": "0.0.1",
  "description": "Projet TP 2",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "tp",
    "node",
    "js"
  ],
  "author": "Thomas CILES",
  "license": "ISC"
}
```

## Installer un dépendance

Une dépendance:

`npm i french-ssn`

Une dépendance de développement:

`npm i -D eslint` 

Cela à pour effet de rajouter les dépendances dans le fichier `package.json` dans les sections `dependencies` et `devDependencies` :

```json
// ....
  "dependencies": {
    "react": "^19.0.0",
    "react-dom": "^19.0.0"
  },
  "devDependencies": {
    "typescript": "~5.6.2"
  },
// ....  
```

de créer un fichier `package-lock.json` avec les metadata(version, checksum, url...) des packages installés. Ce fichier est autogénéré et ne doit pas être modifier.

```json
// ...
    "node_modules/react": {
      "version": "19.1.0",
      "resolved": "https://registry.npmjs.org/react/-/react-19.1.0.tgz",
      "integrity": "sha512-FS+XFBNvn3GTAWq26joslQgWNoFu08F4kl0J4CgdNKADkdSGXQyTCnKteIAJy96Br6YbpEU1LSzV5dYtjMkMDg==",
      "license": "MIT",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/react-dom": {
      "version": "19.1.0",
      "resolved": "https://registry.npmjs.org/react-dom/-/react-dom-19.1.0.tgz",
      "integrity": "sha512-Xs1hdnE+DyKgeHJeJznQmYMIBG3TKIHJJT95Q58nHLSrElKlGQqDTR2HQ9fx5CN/Gk6Vh/kupBTDLU11/nDk/g==",
      "license": "MIT",
      "dependencies": {
        "scheduler": "^0.26.0"
      },
      "peerDependencies": {
        "react": "^19.1.0"
      }
    },
// ...    
```

enfin un dossier `node_modules` a été créé et contient le code source des modules.
