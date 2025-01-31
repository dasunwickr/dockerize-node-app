# Setting Up the Node.js App (Without Docker)

## Introduction
This guide will help you set up and run a simple Node.js Express server without Docker. If you are new to Node.js, follow these steps carefully to get the application up and running.

## Cloning the Repository
Start by cloning the project repository from GitHub:
```sh
git clone https://github.com/dasunwickr/dockerize-node-app.git
cd dockerize-node-app
```

Switch to the `without-docker` branch, which contains the base Node.js application:
```sh
git checkout without-docker
```

## Installing Node.js and npm
Before running the application, ensure that you have Node.js installed.
- **Windows/macOS**: Download and install Node.js from [nodejs.org](https://nodejs.org/).
- **Linux (Debian/Ubuntu)**:
  ```sh
  sudo apt update
  sudo apt install nodejs npm -y
  ```

Verify installation:
```sh
node -v
npm -v
```

## Installing Dependencies
Once Node.js is installed, navigate to the project directory and install the necessary dependencies:
```sh
npm install
```
This will install all the packages listed in `package.json`.

## Running the Node.js Server
Start the server by running:
```sh
npm start
```

If successful, you should see an output like this:
```sh
Server running on port 3000
```

## Testing the Application
Open your browser or use a tool like `curl` or Postman to visit:
```
http://localhost:3000
```
You should see the response:
```
Hello, Docker!
```

## Stopping the Server
To stop the running server, press `Ctrl + C` in the terminal.

## Next Steps
Once you're comfortable running the app locally, you can move on to Dockerizing it by following the `dockerized` branch instructions.

Happy coding! 🚀

