---
title: Tokeninfo-Endpoint
sidebar: sidebar1
permalink: oauthprovider_tokeninfoapi.html
folder: oauthprovider
---

## Introduction

The Tokeninfo API returns information about a given token, if the token is valid.

## URL

The URL is `https://somedomain.com/index.php?oauth-tokeninfo` or `https://somedomain.com/oauth-tokeninfo/`.

## Request Format

Only `POST` requests should be used for accessing this endpoint. Also, this endpoint accepts a content type of `application/x-www-form-urlencoded` only.

The following parameters are required:

| Name | Description |
|------|-------------|
|`access_token` | the access token/JWT token you want information about |


## Example Request

```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-tokeninfo/', array(
	'access_token' => 'aa7c87e3595cc9ae1f04a4cf7769a8ccb972b99931a542e2aedecd9428aa7d8c18d6f16b2fa96020b4cf5aff44d8ce87bdec', 
), "application/x-www-form-urlencoded; charset=utf-8");
```

## Response Format

The response has `JSON` format. If the supplied token is invalid, the response header is `404 Not Found`.

## Example Response for Bearer Token


```json
{ 
   "sub": 1,
   "aud": 1421589198,
   "scope":"identify email profile",
   "exp" : 1569163229,
   "type": "bearer"
}
```

## Example Response for JWT Token

```json
{ 
   "sub":1,
   "aud":"1307734008",
   "scope":"openid email",
   "type":"jwt",
   "exp":1571559438,
   "iss":"http:\/\/somedomain.com\/",
   "iat":1571555838,
   "nbf":1571555778,
   "name":"root",
   "email":"admin@admin.de"
}
```


{% include links.html %}
