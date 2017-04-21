# Core endpoints (built-in features)

Apiko contains some out-of-box features that are often incorporated with APIs and are available for use without any additional requirements. The point of this article is to briefly introduce you to these features, while detailed documentation of each of the mentioned endpoints can be found on your local API server at the `/apiko/reference` endpoint or within the **developer UI**.

## Users

First, a user can be registered by a request to `POST /users`. It is strongly recommended that email addresses are used as usernames (login names).

Normally during a user registration process applications need to check whether a user with a given username exists or not (in order to prevent double registration or other purposes). The endpoint `GET /users/exists/:username` is dedicated for this use.

Then a user can be logged in by a request to `POST /users/login`. On a successful login, this endpoint responds with an access (session) **token** and information about the user themself. Apiko will attempt to set the **token** as a cookie in the `POST /users/login` response and if it succeeds, the token will be then sent with every subsequent request to the Apiko server by the client webbrowser/webview automatically, which will identify the user. If Apiko will fail to set the cookie, you will need to attach the **token** in a `token` parameter (for example as a GET parameter or in the request body) with any following request in order to identify the user.

A user profile can be obtained by a request to `GET /users/:id`.

Update to a user profile can be performed with `PUT /users/:id`.

A user password can be changed with the `POST /users/password/change/:id` endpoint.

Literal logout is [not available](https://github.com/apiko-rest-api/apiko/issues/74). Switch between users can be performed by another request to `POST /users/login` (even while a user is actively logged in).

It is generally considered a better practice to deactivate users rather than deleting them, so the `DELETE /users` endpoint is not implemented by default.

If a user forgets their password, the 'POST /users/password/reset/:id' can be used to send a password reset email (in case the user's `username` property contains a valid email address). This endpoint generates a new random password, which will allow the user to log into their account and change their password in the settings (if your application will allow it).

A list of existing users can be retrieved with `GET /users`.

## Files

To be written...
