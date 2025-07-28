---
category: Javascript
---

# Express 

## Qu'est-ce que c'est ?
[Express](https://expressjs.com/)

ExpressJS est un module qui rajoute une surcouche au module de base `node:http` de NodeJS qui permet de créer facilement une api/application web. En effet Express incorpore nativement un système de routing et de middleware.

## Exemple
```js
const express = require('express');

// Init
const app = express();
const port = 3000;

const users = [
    {id: 1, firstname: "test1", lastname: "test1", email: "test1@gmail.com", role: 'user'},
    {id: 2, firstname: "test2", lastname: "test2", email: "test2@gmail.com", role: 'user'},
    {id: 3, firstname: "test3", lastname: "test3", email: "test3@gmail.com", role: 'user'},
    {id: 4, firstname: "test4", lastname: "test4", email: "test4@gmail.com", role: 'user'},
    {id: 5, firstname: "admin1", lastname: "admin1", email: "admin1@gmail.com", role: 'admin'},
    {id: 6, firstname: "admin2", lastname: "admin2", email: "admin2@gmail.com", role: 'admin'},
];

// Routing/Handling
app.get('/', (req, res) => {
    res.send({
        "/users": {
            method: 'GET',
            description: "List users",
            url: `http://localhost:${port}/users` 
        },
        "/users/:id": {
            method: 'GET',
            description: "Get user informations",
            url: `http://localhost:${port}/users/:id`,
            params: {
                ':id': {
                    type: 'integer',
                    required: true
                }
            } 
        },
        "/users/role/admin": {
            method: 'GET',
            description: "List admin users",
            url: `http://localhost:${port}/users/role/admin` 
        },
        "/users/role/user": {
            method: 'GET',
            description: "List default users",
            url: `http://localhost:${port}/users/role/user` 
        },
    }) 
});

app.get('/users', (req, res) => {
    res.json(users);
});


app.get('/users/:id{}', (req, res) => {
    const id = Number.parseInt(req.params.id || "-1");
    const user = users.find((u) => u.id === id);

    if (user) {
        return res.json(user);
    }

    res.status(404).json({
        success: false,
    });
});

app.get('/users/role/:role{admin|user}', (req, res) => {
    const role = req.params.role;
    res.json(users.filter(u => u.role === role ));
});

// Start
app.listen(port, () => {
    console.log(`Example app listening on port ${port}`)
});
```


