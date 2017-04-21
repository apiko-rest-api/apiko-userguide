# Installation and setup

## Installing the CLI tool

To help you get started with Apiko, we've built a convenient CLI tool. Get it using [NPM](https://docs.npmjs.com/getting-started/installing-node):

`npm i -g apiko-cli`

It will take a while to install, then you are ready to use the Apiko CLI tool to setup your first project.

## First setup and run

Use the Apiko CLI to create a new Apiko API server project for you:

`apiko setup myapiserver`

This command will:

1. Create a new directory called `myapiserver` (or name of your choice) in the current working directory.
2. Download a starter Apiko project and configuration in it.
3. Install all required NPM modules.
4. Start Apiko.

These steps will take a while, so be patient. Ultimately you should end up with a message saying that Apiko is listening on port 5000.

Next you should be able to view the Apiko's configuration (developer) UI at [http://localhost:5000/dev/](http://localhost:5000/dev/). You can use this UI to:

- Create and manage database collections / tables.
- Configure endpoints (URLs & HTTP methods) available in your API, some core endpoints are already included.
- Configure endpoint parameters and their validation.
- Configure access to the available endpoints.
- Document your endpoints along with generated documentation.

## Next run

Whenever you want to start the Apiko server next time. Change to the project's directory (`cd myapiserver`) and run:

`apiko run dev`

Where `dev` can be swapped for your environment set of configuration (`dev` or `prod` with the starter configuration).

## Testing endpoints

All the endpoints you can see in the Apiko configuration / developer UI are by default available under http://localhost:5000/...

You can use a REST API testing tool of your choice.

## What's next

- With the starter configuration, the server data are stored in an SQLite database (which can be found as a file in the project's root directory). You may want to set up your Apiko server for a different kind of database, see the [Configuration](Configuration.md) page for more information.
- Apiko contains several built-in features for you to save your time, have a look at the [core endpoints](Core%20endpoints%20(built-in%20features).md).
- Once you need to move beyond the Apiko's out of box features that can be set up using the **developer UI** and configuration file, [custom endpoint handlers](Custom%20endpoint%20handlers.md) are a way to go.
