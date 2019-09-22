---
title: Token-Endpoint
sidebar: sidebar1
permalink: oauthprovider_tokenapi.html
folder: oauthprovider
---

## Introduction

The Token-Endpoint exchanges the authorisation code into an user's access token.

## URL
You can get the URL for the Token-Endpoint when editing the OAuth-Client.

## Request Format

Only `POST` requests should be used for accessing this endpoint. Also, this endpoint accepts a content type of `application/x-www-form-urlencoded` only.

The following parameters are required:

| Name | Description |
|------|-------------|
|`client_id` | your application's client id |
|`client_secret` | your application's client secret |
|`grant_type` | must be set to `authorization_code` |
|`code` | the code from the querystring |
|`redirect_uri` | your redirect_uri |
|`scope` | the scopes requested in your authorization url, space-delimited |



## Example Request

```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-token/', array(
	'client_id' => '1421589198', 
	'client_secret' => 'C7LxkuPm0a7JozCd16cyiKLA31UHqbwdUZPxX8auDDO3uiiFqa1Q7SRObHtLsd2k9pmYZqmAqKBlkf3ThCtScMSTzhz9DSfjW7GP0DAfNaWO0ZXNT8SzNqWO6yTfwVq7', 
	'grant_type' => 'authorization_code', 
	'code' => 'aa7c87e3595cc9ae1f04a4cf7769a8ccb972b99931a542e2aedecd9428aa7d8c18d6f16b2fa96020b4cf5aff44d8ce87bdec', 
	'scope' => 'identify email', 
	'redirect_uri' => 'http://localhost/'), "application/x-www-form-urlencoded; charset=utf-8");
```

## Response Format

The response has JSON format.

## Example Response


```
{ 
   "access_token":"a959083fccacea34e1ecdc9acf4ab24b38c9aacd317f0c3bf9e1ae51b25a5a5b10b92174d4327c60024307605e5d927c1a4bca1da94040a76f6c12be6e85a8a9457d83039068",
   "token_type":"Bearer",
   "expires_in":3600,
   "scope":"identify email"
}
```


{% include links.html %}
