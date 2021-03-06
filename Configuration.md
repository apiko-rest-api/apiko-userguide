# Configuring Apiko

There are two kinds of Apiko configuration: **Apiko setup** and the actual **Apiko configuration**. This document is more about the later one.

## Apiko setup

Apiko setup is what you can edit and configure in the **developer UI**, which is installed with every Apiko server and can be opened at the `/dev` endpoint (e.g. [http://localhost:5000/dev/](http://localhost:5000/dev/) with the starter configuration). It includes:

- Creation of database collections / tables.
- Configuration of endpoints (URLs & HTTP methods) available in your API.
- Configuration of endpoint parameters and their validation.
- Configuration of access to the available endpoints.
- Documentation of your endpoints.

There's a question mark icon **(?)** in the developer UI menu that turns on and off the in-place documentation, which should help you with setting up everything mentioned.

These are the things you configure the most often in Apiko (it's the definition of your API) and that's why the developer UI exists - to make it simple and fast for you. Chances are good that you are already viewing this guide from the developer UI.

In fact the output of the developer UI is what we call **Apiko setup** (as mentioned earlier) and is stored in a **JSON format that you should never need to understand** in the `apiko.json` file in your project's root directory.

# Apiko configuration

## Environments

Whenever you start the Apiko server using the CLI tool:

`apiko run <environment>`

What you pass in the **environment** argument is what you will receive as the third argument in your **main.js** file. With this in mind, you can then use simple `if` to define different configurations for different environments, for example:

```
var Apiko = require('apiko')

var config = {
  port: 5000
}

if (process.argv[2] === 'prod') {
  // ...
}

if (process.argv[2] === 'dev') {
  config.protect = false
  config.verbosity = 2
}

Apiko.run(config)
```

Note: The starter configuration contains `prod` and `dev` environments, but you can define any amount of environments with any names.

## Configuration options

The configuration object passed to the `Apiko.run(options)` function may contain the following options:

### db

<table>
<thead><tr><th>Type</th><th>Default</th></tr></thead>
<tbody><tr><td>Object</td><td>
{
  dialect: 'sqlite',
  host: 'localhost',
  user: 'root',
  pass: 'root',
  storage: 'datastore.sqlite'
}
</td></tr></tbody>
</table>

Database configuration option - is an object, which may contain the following properties:

<table>
<thead><tr><th>Property</th><th>Type</th><th>Default</th><th>Description</th></tr></thead>
<tbody>
  <tr><td>dialect</td><td>String</td><td>'sqlite'</td><td>Database type to connect to.</td><td></td></tr>
  <tr><td>host</td><td>String</td><td>'localhost'</td><td>Database server address to connect to.</td><td></td></tr>
  <tr><td>user</td><td>String</td><td>'root'</td><td>Database user to connect with.</td><td></td></tr>
  <tr><td>pass</td><td>String</td><td>'root'</td><td>Database password to connect with.</td><td></td></tr>
  <tr><td>storage</td><td>String</td><td>'datastore.sqlite'</td><td>Database file to open (SQLite only).</td><td></td></tr>
</tbody>
</table>

Apiko uses the [Sequelize.js library](https://github.com/sequelize/sequelize) for database management. Sequelize supports the following database dialects: `sqlite`, `mysql`, `mariadb`, `postgres`, `mssql` (any of these can be the value of the `dialect` property). For any database dialect other than `sqlite` the `host`, `user` and `pass` properties have to be specified. For the `sqlite` database dialect the `storage` property has to be specified supplying the name of the database file, which will be created under your API server's project root.

### filesDirectory

<table>
<thead><tr><th>Type</th><th>Default</th></tr></thead>
<tbody><tr><td>String</td><td>'files'</td></tr></tbody>
</table>

Sets a directory name in which the uploaded files will be stored. This directory will be automatically created under your API server project's root.

### port

<table>
<thead><tr><th>Type</th><th>Default</th></tr></thead>
<tbody><tr><td>Number</td><td>5000</td></tr></tbody>
</table>

The port to run Apiko on. Should be higher than 1024, make sure it is available on your system.

### prefix

<table>
<thead><tr><th>Type</th><th>Default</th></tr></thead>
<tbody><tr><td>String</td><td>(no prefix)</td></tr></tbody>
</table>

Puts all your endpoints after a prefix. For example, if `api` (**no slashes!**) will be the value of this option, all your endpoints will be under `http://localhost:5000/api/...` with the starter configuration.

### protect

<table>
<thead><tr><th>Type</th><th>Default</th></tr></thead>
<tbody><tr><td>Boolean</td><td>true</td></tr></tbody>
</table>

If true, sensitive core Apiko endpoints have to be requested with a `secret` parameter containing the server's secret (which can be found in `apiko.json`). This protects your API server from being manipulated by anyone who doesn't know the *secret*, you should set this option to `true` for production.

### verbosity

<table>
<thead><tr><th>Type</th><th>Default</th></tr></thead>
<tbody><tr><td>Number</td><td>1</td></tr></tbody>
</table>

Defines how detailed messages should be output while Apiko server is running. Can be a number between 0 and 3:

<table>
<thead><tr><th>Log level</th><th>Description</th></tr></thead>
<tbody><tr><td>0</td><td>Only fatal errors</td></tr></tbody>
<tbody><tr><td>1</td><td>Important runtime messages and errors</td></tr></tbody>
<tbody><tr><td>2</td><td>All runtime messages, warnings and errors</td></tr></tbody>
<tbody><tr><td>3</td><td>Everything, including dumps and database queries</td></tr></tbody>
</table>
