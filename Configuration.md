# Configuring Apiko

There are two kinds of Apiko configuration: **Apiko setup** and the actual **Apiko configuration**. This document is more about the later one.

## Apiko setup

Apiko setup is what you can edit and configure in the **developer UI**, which is installed with every Apiko server and can be opened at the `/dev` endpoint (e.g. [http://localhost:5000/dev/](http://localhost:5000/dev/) with the starter configuration). It includes:

- Creation of database collections / tables.
- Configuration of endpoints (URLs & HTTP methods) available in your API.
- Configuration of endpoint parameters and their validation.
- Configuration of access to the available endpoints.
- Documentation of your endpoints.

There's a question mark icon (?) in the developer UI menu that turns on and off the in-place documentation, which should help you with setting up everything mentioned.

These are the things you configure the most often in Apiko (it's the definition of your API) and that's why the developer UI exists - to make it simple and fast for you. Chances are good that you are already viewing this guide from the developer UI.

In fact the output of the developer UI is what we call **Apiko setup** (as mentioned earlier) and is stored in a **JSON format that you should never need to understand** in the `apiko.json` file in your project's root directory.
