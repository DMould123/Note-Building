# Express.js API Server 🚀

## Introduction

This guide will walk you through setting up and using a simple API server using Express.js.

## Getting Started!

### Step 1 - Project Setup in VSC

Create a new directory for your Express.js project and set it up by running these commands in your terminal on VSC.

```
mkdir express-api-server
cd express-api-server
npm init -y
npm install express nodemon
```

### Step 2 - Project Structure
Ensure your project directory is structured as follows:

```
express-api-server/
├── public/
│   └── index.html
└── server.js
```
### Step 3 - Server Setup
Create a server.js file and set up your Express.js server:

```
const express = require('express');
const app = express();
const port = 4000;

// middleware
app.use(express.json());
app.use(express.static('public'));

// DATABASE TEST
const db = [];

// GET
app.get('/', (req, res) => {
  console.log('Home route: GET');
  res.status(200).send('Hej ');
});

// POST
app.post('/api/info', (req, res) => {
  const { info } = req.body;
  console.log('You posted: ', info);
  db.push(info);
  console.log('DB: ', db);
  res.status(201).json({ yourMessageHere: info });
});

// PUT
app.put('/api', (req, res) => {
  const { info } = req.body;
  console.log(info);
  res.status(200).send();
});

// DELETE. all dynamic routes should be at the bottom
app.delete('/delete/:id/:name', (req, res) => {
  const { id, name } = req.params;
  console.log('You sure you want to delete?', id, name);
  res.status(200).send();
});

app.listen(port, () => console.log(`Server has started on port: ${port}`));

```

### Step 4 - HTML Setup
Create an index.html file in the public directory with the following content:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Document</title>
</head>
<body>
  PRESS ME
  <button id="test-button">Press Me</button>
</body>
<script>
  const btn = document.getElementById('test-button');
  async function sendMsg() {
    const res = await fetch('/api/info', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ info: 'SENT FROM THE WEB CLIENT' }),
    });
    console.log('request sent');
  }
  btn.addEventListener('click', sendMsg);
</script>
</html>
```

### Step 5 - Running the Server
Run your server by executing:

```
nodemon server.js
```

### API Endpoints
```
- GET /: Serves the home route.
- POST /api/info: Accepts JSON data and stores it in an in-memory database.
- PUT /api: Logs the received data.
- DELETE /delete/
/
: Logs the id and name parameters from the URL.
```

## Conclusion
You've set up a basic API server using Express.js. Customize the routes and functionality as needed for your application. Happy coding!
