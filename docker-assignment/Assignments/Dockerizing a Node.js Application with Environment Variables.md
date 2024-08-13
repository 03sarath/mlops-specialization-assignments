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
  res.send(greeting);
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








