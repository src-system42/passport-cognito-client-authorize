# Passport Cognito Client Authorize

## Overview

AWS Cognito provides a REST interface for authenticating and generating tokens for its user pools.  This project allows a user to easily configure and request access tokens locally (helpful for cURL commands, for example).

Using these APIs will require some knowledge of OAUTH2 and authorization flows such as [authorization code grant](https://auth0.com/docs/api-auth/tutorials/authorization-code-grant).

## Getting started

* Clone this repository.
* Ensure you have NodeJS and NPM installed.
* Run `npm install` to download the necessary libraries.
* Make a configuration file called `config.json` in the root directory. You can use `default-config.json` to help you scaffold this out.

## Running

Once you have a configuration file set up, run `npm start` and an express app will run on `localhost:4200` exposing a `GET: /cognito/token` route.  The response will be an access token as text.

## Example

1. Start the Express server by running: `npm start`.  It should be available at `localhost:4200/cognito/token`.
2. Pipe the token to a cURL command for authorization:
```bash
# Insert token into authorization header after execution
curl -H "Authorization: Bearer $(curl localhost:4200/cognito/token)" https://my.authorized.api/rest/protected/route
```

## Configuration

The example configuration looks like:

```json
{
    "poolId": "<pool ID>",
    "clientId": "<client ID>",
    "region": "<region>",
    "username": "username",
    "password": "password",
    "port": 4200
}
```

* `poolId`: The ID of the Cognito pool.
* `clientId`: The ID of the Cognito client (must enable auth code flow). 
* `region`: The region of the AWS account where the pool is located.
* `username`: The username of a registered user in the pool.
* `password`: The password of a registered user in the pool.
* `port (Optional)`: The port the server runs on - default 4200.

## Copyright
MIT (c) 2018 Matt Johnson - Cedrus, LLC.