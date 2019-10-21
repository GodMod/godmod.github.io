---
title: Authorization-Endpoint
sidebar: sidebar1
permalink: oauthprovider_consent.html
folder: oauthprovider
---

## Introduction

The Authorization-Endpoint shows an page to the User with the requested scopes. The user must authorize the application before the user is returned to the Client application.

## URL
You can get the URL for the Authorization-Endpoint when editing the OAuth-Client.

## Scopes

The following scopes can be requested.

| Name | Description |
|------|-------------|
|`identify` | User-ID, Username and Avatar |
|`openid` | Same as `identify`, but used for OpenID Connect. Will also return an JWT Token at the Token Endpoint, if reponse_type `code` was choosen |
|`email` | Email-address of the user |
|`profile` | Profile-Information of the user |


## Request Format

The following parameters are required:

| Name | Description |
|------|-------------|
|`client_id` | your application's client id |
|`scope` | the scopes you want to request, space-delimited |

The following parameters are optional:

| Name | Description |
|------|-------------|
|`redirect_uri` | Your redirect_uri, urlencoded. Default: the one saved with the OAuth Client |
|`response_type` | `code` will return authorization code, `token` will return access token (if implicit grant is allowed), `id_token` will return JWT-Token (if implicit grant is allowed). Default: `code` |
|`state` | a custom state from your application. Please see next chapter for using this param for security purposes |
|`nonce` | a custom random value from your application, which will be included in an ID Token |

## State and Security

The `state` param can be used to prevent CSRF and Clickjacking vulnerabilities. 
`state` is sent in the authorization request and returned back in the response and should be a value that binds the user's request to their authenticated `state`. For example, state could be a hash of the user's session cookie, or some other nonce that can be linked to the user's session.
When a user begins an authorization flow on the client, a `state` is generated that is unique to that user's request. This value is stored somewhere only accessible to the client and the user, i.e. protected by the same-origin policy. When the user is redirected, the `state` parameter is returned. The client validates the request by checking that the `state` returned matches the stored value. If they match, it is a valid authorization request. If they do not match, it's possible that someone intercepted the request or otherwise falsely authorized themselves to another user's resources, and the request should be denied.
While the use of the `state` parameter is not required, it is highly recommend that you implement it for the security of your own applications and data.

## Example Request

Example Request for authorization code: 

```php
https://test.eqdkp-plus.eu/wcf/oauth-consent/?client_id=1421589198&redirect_uri=https://somedomain.com/oauth-return/&scope=identify+email+profile&state=d927c1a4bca1da94040&response_type=code
```

Example Request for access token (Implicit Grant type must be enabled for your OAuth Client):

```php
https://test.eqdkp-plus.eu/wcf/oauth-consent/?client_id=1421589198&redirect_uri=https://somedomain.com/oauth-return/&scope=identify+email+profile&state=d927c1a4bca1da94040&response_type=token
```

Example Request for JWT token (Implicit Grant type must be enabled for your OAuth Client):

```php
https://test.eqdkp-plus.eu/wcf/oauth-consent/?client_id=1421589198&redirect_uri=https://somedomain.com/oauth-return/&scope=identify+email+profile&state=d927c1a4bca1da94040&response_type=id_token
```

## Response Format

As response, the user is redirected to your application, explicit to your given `redirect_uri`. The code or token are added as parameter to the URL.

## Example Response

Example Response for access token:

```html
https://somedomain.com/oauth-return/?code=ec7be46a4925ed5c8f1204c2a904827a7b07f3d8b3af8164d640be0f1f3e9b84e84b67d44546bf61a2f505e4759de9520fb0&state=d927c1a4bca1da94040
```

Example Reponse for Access Token (Implicit Flow):
```html
https://somedomain.com/oauth-return/#access_token=a959083fccacea34e1ecdc9acf4ab24b38c9aacd317f0c3bf9e1ae51b25a5a5b10b92174d4327c60024307605e5d927c1a4bca1da94040a76f6c12be6e85a8a9457d83039068&state=d927c1a4bca1da94040
```

Example Response for JWT Token (Implicit Flow):

```html
https://somedomain.com/oauth-return/#id_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL3NvbnN0aWdlXC9mb3J1bTUuMS43XC91cGxvYWRcLyIsImF1ZCI6Imh0dHA6XC9cL2xvY2FsaG9zdFwvc29uc3RpZ2VcL2ZvcnVtNS4xLjdcL3VwbG9hZFwvIiwiaWF0IjoxNTY5MTYxNDI5LCJuYmYiOjE1NjkxNjEzNjksImV4cCI6MTU2OTE2MzIyOSwiZGF0YSI6eyJjbGllbnRJRCI6IjE0MjE1ODkxOTgiLCJzY29wZSI6ImlkZW50aWZ5IGVtYWlsIHByb2ZpbGUiLCJ1c2VySUQiOjEsInVzZXJuYW1lIjoicm9vdCIsImVtYWlsIjoiYWRtaW5AYWRtaW4uZGUifX0.8agUuQAqoqBRHo5wHJRQMtSJHmvNfVBd7s1eURdVHw8&state=d927c1a4bca1da94040
```

## JWT-/ID-Token

The returned JWT Token has three sections: header, payload and the signature.

The header contains the used algorithm and token type. Currently, only the HS256 algorithm is supported.

```json
{
  "typ": "JWT",
  "alg": "HS256"
}
```

The payload contains the following data:

```json
{
  "iss": "https://test.eqdkp-plus.eu/",
  "aud": "1307734008",
  "iat": 1569161429,
  "nbf": 1569161369,
  "exp": 1569163229,
  "sub": 1,
  "name": "root",
  "nonce": "e4a17ae2bd26b09bad86b902e990a252",
  "scope": "openid email",
  "email": "admin@admin.de"
}
```
The payload will never contain the profile information, even if it was requested. You can use the User-API to request the profile information, by passing the JWT-Token as access token.

The last part of the JWT Token is the signature. As key, the JWT-Secret of your OAuth-Client is used.
So you can use the JWT-Secret to prove the signature. Also, the parts like `iss`, `iat`, `nbf` and `exp` should be checked by your application.


{% include links.html %}
