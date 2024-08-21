# Assignment 2: Dockerizing a Node.js Application with Environment Variables

#### Task
Create a Node.js application that reads configuration values from environment variables. The application should display a message that includes a configurable environment variable. Dockerize the Node.js application.

Tips: 
1. Create the Node.js Application:
2. Create a directory for your project and add the following files `app.js:`, `package.json`

```
const express = require('express');

const app = express();
const port = process.env.PORT || 3000;
const greeting = process.env.GREETING || 'Hello, Docker!';

app.get('/', (req, res) => {
  res.send(`
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Travel App</title>
      <style>
        body {
          font-family: Arial, sans-serif;
          margin: 0;
          padding: 0;
          background-color: #f4f4f4;
          color: #333;
          text-align: center;
        }
        header {
          background-color: #333;
          color: #fff;
          padding: 10px 0;
        }
        header h1 {
          margin: 0;
        }
        nav {
          margin: 20px 0;
        }
        nav a {
          color: #fff;
          text-decoration: none;
          margin: 0 10px;
        }
        nav a:hover {
          text-decoration: underline;
        }
        main {
          padding: 20px;
        }
        footer {
          background-color: #333;
          color: #fff;
          padding: 10px 0;
          position: absolute;
          bottom: 0;
          width: 100%;
        }
      </style>
    </head>
    <body>
      <header>
        <h1>Travel App</h1>
        <nav>
          <a href="/">Home</a>
          <a href="/destination/paris">Paris</a>
          <a href="/destination/tokyo">Tokyo</a>
          <a href="/destination/new-york">New York</a>
        </nav>
      </header>
      <main>
        <p>You're environment variable display here👇:</p>

        <h2>Welcome to <b style="color:red">${greeting}</b> Travel App!</h2>
      
      </main>
      <footer>
        <p>&copy; 2024 Travel App</p>
      </footer>
    </body>
    </html>
  `);
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}/`);
});


```
 `package.json`

 ```
{
    "name": "node-env-app",
    "version": "1.0.0",
    "main": "app.js",
    "scripts": {
      "start": "node app.js"
    },
    "dependencies": {
      "express": "^4.18.2"
    }
  }
  
 ```

3. Create the Dockerfile:
```
# Use the official Node.js image from the Docker Hub

# Set the working directory in the container

# Copy package.json and install dependencies

# Copy the application code into the container

# Expose port 3000

# Command to run the Node.js app

```

4. Build, Run and Push the Docker Image:

Run the Docker Image with Environment Variables

```docker run -e GREETING="Welcome to Docker!" -p 3000:3000 node-env-app```

The `-e` flag in the Docker command is used to set environment variables inside the Docker container. When you run a Docker container with the -e option, you can define environment variables that your application can use at runtime.








