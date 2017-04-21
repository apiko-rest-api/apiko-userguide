# Serving frontend with Apiko

Each newly setup Apiko project (`apiko setup <directory>`) contains a `www` directory. If you wish to serve your front-end files using Apiko (without the use of a third party web server), you can put any static files (HTML, CSS, JavaScript, images and other files) to this `www` directory.

**Warning:** Your files and directories under `www` **override** any endpoints defined in Apiko. It is recommended (but not set up with the starter configuration) to put all your endpoints under an API prefix, e.g. `http://localhost:5000/api/...`. Please see the **prefix** configuration option on the [Configuration](Configuration.md) page for more details.

**Note:** Apiko currently doesn't support complex routing. For routing with SPA frameworks, you will need to put the route after `#`, e.g. `#/home`.
