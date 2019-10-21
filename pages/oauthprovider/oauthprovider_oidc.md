---
title: OpenID Connect (OIDC)
sidebar: sidebar1
permalink: oauthprovider_oidc.html
folder: oauthprovider
---

## Introduction

The Plugin supports the OpenID Connect flow.

## Discovery URL
The URL is for fetchting the Discovery inforation is `https://somedomain.com/index.php?openid-discovery` or `https://somedomain.com/openid-discovery/`.

You can also copy the output of the site (JSON) into a file named `https://somedomain.com/.well-known/openid-configuration`. Please add no folder into this path, even if your WSC is installed in a subfolder.

## Example Discovery Output
```json
{ 
   "issuer":"http:\/\/somedomain.com\/",
   "authorization_endpoint":"http:\/\/somedomain.com\/index.php?oauth-consent\/",
   "token_endpoint":"http:\/\/somedomain.com\/index.php?oauth-token\/",
   "userinfo_endpoint":"http:\/\/somedomain.com\/index.php?oauth-user\/",
   "scopes_supported":[ 
      "openid",
      "identify",
      "email",
      "profile"
   ],
   "response_types_supported":[ 
      "code",
      "token",
      "id_token"
   ],
   "id_token_signing_alg_values_supported":[ 
      "HS256"
   ],
   "subject_types_supported":[ 
      "public"
   ],
   "token_endpoint_auth_methods_supported":[ 
      "client_secret_post",
      "client_secret_basic"
   ],
   "jwks_uri":"https:\/\/www.googleapis.com\/oauth2\/v3\/certs",
   "claims_supported":[ 
      "aud",
      "email",
      "exp",
      "iat",
      "iss",
      "name",
      "sub",
      "nonce",
      "nbf",
      "data",
      "preferred_username",
      "picture",
      "scope",
      "profile"
   ]
}
```

## Response types
As you can see from the Discovery File, the following return types are supported:
* code
* token - *Implicit Flow, must be enabled for the client*
* id_token - *Implicit Flow, must be enabled for the client*

## Signing Algorithms
In contract to the OpenID specifications, we do not Support RS256 algorithm, but only HS256. Most libraries will also support the HS256 algorithm. For validation of the JWT Token, the Client-Secret should be used for the HS256 algorithm.



{% include links.html %}
