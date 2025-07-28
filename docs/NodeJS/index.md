# NodeJS

Créé par [Ryan Dahl](https://en.wikipedia.org/wiki/Ryan_Dahl) en 2009.
C'est un environnement d'éxecution Javascript multi-plateforme, permettant d'exécuter du javascript en dehors d'un contexte navigateur
(par exemple: en mode serveur...).

## Installation
### Windows
### MacOS
### Linux


## Determiné le type de gestion de module
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
 