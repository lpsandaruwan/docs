# Creating a new Colyseus Server

**Requirements**:

- [Download and install Node.js](https://nodejs.org/) v14.0 or higher
- [Download and install Git SCM](https://git-scm.com/downloads)
- [Download and install Visual Studio Code](https://code.visualstudio.com/) (or other editor of your choice)

## Creating a Colyseus server from NPM template

Use the `npm init colyseus-app` command to generate a barebones Colyseus server. You may select between TypeScript (recommended) and JavaScript as the language for the server. These are the only two languages currently supported by **Arena Cloud**.

```
npm init colyseus-app ./my-colyseus-app
```
![NPM Selection](../../images/arena-app-support.jpg)

- ONLY Complied **TypeScript** and **JavaScript (CommonJS)** are currently supported. *ESM support is coming soon.*

The following is the expected folder structure and files that are created in the *my-colyseus-app* directory for a TypeScript server.

![NPM Code](../../images/new-arena-server-code.jpg)

- **index.ts / js:** This file is used for local testing or self-hosting. To ensure Arena Cloud complatitablity we ***recommend*** that you make ***NO*** changes to the index file directly. Changes or functionality added here will not be reflected when your server is hosted on Arena Cloud. For local testing you can modifiy this file to change the Colyseus server port.

- **arena.config.ts / js:** On this file you can make additions and modifications required to support your game. Take note of the three core functions that will be called during the initialization of your game server.

```
    getId: () => "Your Colyseus App",

    initializeTransport: (options) => {
        /**
         * Define your server transports as uWS (latest)
         */
        return new uWebSocketsTransport({});

        /**
         * Define your server transports as Legacy WS (legacy)
         * For local development with Legacy WS you will need to
         * provide the server option below, this is not required on Arena
         */
        // return new WebSocketTransport({
        //     ...options,
        //     pingInterval: 5000,
        //     pingMaxRetries: 3,
        // });
    },

    initializeGameServer: (gameServer) => {
        /**
         * Define your room handlers:
         */
        gameServer.define('my_room', MyRoom);

    },

    initializeExpress: (app) => {
        /**
         * Bind your custom express routes here:
         */
        app.get("/", (req, res) => {
            res.send("It's time to kick ass and chew bubblegum!");
        });

        /**
         * Bind @colyseus/monitor
         * It is recommended to protect this route with a password.
         * Read more: https://docs.colyseus.io/tools/monitor/
         */
        app.use("/colyseus", monitor());
    },


    beforeListen: () => {
        /**
         * Before gameServer.listen() is called.
         */
    }
```

- **arena.env / development.env:** These files are used to manage the environmental variable for your Colyseus Server, arena.env will be loaded by default when hosting on Arena Cloud.

- **lib / upload Folder:** This folder will only be created after running ```npm run build``` for the first time. This will contain the complied JS code, package.json and .env files that need to be uploaded to Arena Cloud.
