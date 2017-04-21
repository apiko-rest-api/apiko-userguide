# Custom endpoint handlers

Use the **developer UI** to define a custom endpoint, its parameters and access rules. Then in your API server's code (`main.js` or module files), define the endpoint's handler as follows:

```
var Apiko = require('apiko')

Apiko.on('GET /yourendpoint', (req, res, next) => {
  // the handler logic
  res.success({any: 'data'}) // 200 OK
})

Apiko.run(config)
```

Make sure you specify the right HTTP method (GET, POST, PUT, DELETE...) and URL corresponding with the endpoint you have defined in the developer UI. For example `GET /yourendpoint` and `POST /yourendpoint` are treated as independent endpoints.

The `req` (request) and `res` (response) arguments are [Express.js objects](https://expressjs.com/en/4x/api.html) extended with some Apiko-specific properties (see the API section).

**Important:** each custom handler should be ended with either `res.success()` or `res.error()`.

## Apiko-specific properties

The following properties can be used within any custom endpoint handler:

### res.success(dataObject)

Accepts a JSON object, which will be sent as the response's body along with HTTP status 200.

### res.error(HttpStatusCode, 'CustomMessage', CustomErrorCode)

Will send an error response.

For example `res.error(501, 'This endpoint is not done yet.', 106)` will send the following data in the response's body along with the 501 HTTP status code:

```
{
  "code":106,
  "message":"This endpoint is not done yet."
}
```

The *CustomMessage* and *CustomErrorCode* are desinged to further extend the existing HTTP status codes for the purpose of your application. It is completely optional and up to the demand of the application you are building what information will you provide. `res.error(501, 'This endpoint is not done yet.')` will work as well as just `res.error(501)`. For *CustomErrorCode* it is recommended to choose a number over 100 since some core endpoints use error numbering below 100.

### req.all

An object containing **all request parameters combined**.

There are 3 types of request parameters an endpoint can rececive:
- [Route parameters](https://expressjs.com/en/guide/routing.html#route-parameters) that you may specify in your endpoint URL, for example: `/yourendpoint/:id`. In this case if you later access your endpoint with a value such as `/yourendpoint/33`, then `req.all.id` will contain `33`.
- GET parameters, for example, accessing your endpoint with `/yourendpoint?language=en` will cause `req.all.language` being `en`.
- Request body parameters, Apiko uses the [body-parser](https://www.npmjs.com/package/body-parser) module, which parses *JSON*, *Raw*, *Text* and *URL-Encoded form* bodies.

**Note:** body-parser doesn't parse multipart  by dedault, see their [documentation](https://www.npmjs.com/package/body-parser) for suggestions what to do.

### res.body and res.status

Provide the output of a core handler in case of handler extension. Please see **Overriding core endpoint handlers**.

## Overriding core endpoint handlers

Certain core endpoint handlers can be extended, the following example will extend the default user registration handler:

```
var Apiko = require('apiko')

Apiko.on('POST /users', (req, res, next) => {
  // the handler logic
  res.success({any: 'data'}) // 200 OK
})

Apiko.run(config)
```

After the core handler function is done, it will populate the res.status and res.body properties according to the success or failure of registering a user. You can read these properties to figure out what happened, take an action and end the endpoint's response however your application requires.

## Defining custom handlers without developer UI

Although the **developer UI** is here to make setting up an endpoint easy for you, you can also define an endpoint handler without defining it in using the developer UI.

```
var Apiko = require('apiko')

Apiko.on('GET /yourhandler', (req, res, next) => {
  // the handler logic
  res.success({any: 'data'}) // 200 OK
},
{
  parameter1: {
    required: true,
    regex: '^\\d+$'
  },
  parameter2: {
    required: true,
    regex: '^\\w+$'
  }
})

Apiko.run(config)
```

The example above will create a `GET /yourendpoint` endpoint and will specify two required parameters for it as the third argument of the `Apiko.on()` function, which is optional.
