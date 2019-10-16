---
title: Token-Endpoint
sidebar: sidebar1
permalink: oauthprovider_tokenapi.html
folder: oauthprovider
---

## Introduction

The Token API supports multiple grants:
* authorization_code
* password
* refresh_token

## URL
You can get the URL for the Token-Endpoint when editing the OAuth-Client.

## Authorization-Code Grant Type

This Grant Type exchanges the authorisation code into an user's access token.

### Request Format

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



### Example Request

```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-token/', array(
	'client_id' => '1421589198', 
	'client_secret' => 'C7LxkuPm0a7JozCd16cyiKLA31UHqbwdUZPxX8auDDO3uiiFqa1Q7SRObHtLsd2k9pmYZqmAqKBlkf3ThCtScMSTzhz9DSfjW7GP0DAfNaWO0ZXNT8SzNqWO6yTfwVq7', 
	'grant_type' => 'authorization_code', 
	'code' => 'aa7c87e3595cc9ae1f04a4cf7769a8ccb972b99931a542e2aedecd9428aa7d8c18d6f16b2fa96020b4cf5aff44d8ce87bdec', 
	'scope' => 'identify email profile', 
	'redirect_uri' => 'https://somedomain.com/oauth-return/'), "application/x-www-form-urlencoded; charset=utf-8");
```

### Response Format

The response has `JSON` format.

### Example Response


```json
{ 
   "access_token":"a959083fccacea34e1ecdc9acf4ab24b38c9aacd317f0c3bf9e1ae51b25a5a5b10b92174d4327c60024307605e5d927c1a4bca1da94040a76f6c12be6e85a8a9457d83039068",
   "token_type":"Bearer",
   "expires_in":3600,
   "scope":"identify email profile"
}
```

## Refresh Token Grant Type

This grant type allows getting a new access token by sending an existing refresh token.

### Request Format

Only `POST` requests should be used for accessing this endpoint. Also, this endpoint accepts a content type of `application/x-www-form-urlencoded` only.

The following parameters are required:

| Name | Description |
|------|-------------|
|`client_id` | your application's client id |
|`client_secret` | your application's client secret |
|`grant_type` | must be set to `refresh_token` |
|`refresh_token` | your refresh token |
|`redirect_uri` | your redirect_uri |
|`scope` | the scopes requested in your authorization url, space-delimited |

### Example Request

```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-token/', array(
	'client_id' => '1421589198', 
	'client_secret' => 'C7LxkuPm0a7JozCd16cyiKLA31UHqbwdUZPxX8auDDO3uiiFqa1Q7SRObHtLsd2k9pmYZqmAqKBlkf3ThCtScMSTzhz9DSfjW7GP0DAfNaWO0ZXNT8SzNqWO6yTfwVq7', 
	'grant_type' => 'refresh_token', 
	'refresh_token' => 'aa7c87e3595cc9ae1f04a4cf7769a8ccb972b99931a542e2aedecd9428aa7d8c18d6f16b2fa96020b4cf5aff44d8ce87bdec', 
	'scope' => 'identify email profile', 
	'redirect_uri' => 'https://somedomain.com/oauth-return/'), "application/x-www-form-urlencoded; charset=utf-8");
```

### Response Format
The response has `JSON` format.

### Example Response

```json
{ 
   "access_token":"a959083fccacea34e1ecdc9acf4ab24b38c9aacd317f0c3bf9e1ae51b25a5a5b10b92174d4327c60024307605e5d927c1a4bca1da94040a76f6c12be6e85a8a9457d83039068",
   "token_type":"Bearer",
   "expires_in":3600,
   "scope":"identify email profile"
}
```

## Password Grant Type
This grant type allows exchanging supplied user credentials for an access token. As the user supplies his credentials, all scopes 

### Request Format

Only `POST` requests should be used for accessing this endpoint. Also, this endpoint accepts a content type of `application/x-www-form-urlencoded` only.

The following parameters are required:

| Name | Description |
|------|-------------|
|`client_id` | your application's client id |
|`grant_type` | must be set to `password` |
|`username` | user's username |
|`password` | user's password |

### Example Request
```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-token/', array(
	'client_id' => '1421589198', 
	'grant_type' => 'password', 
	'username' => 'Hillary', 
	'password' => '12345678'), "application/x-www-form-urlencoded; charset=utf-8");
```

### Response Format
The response has `JSON` format.

### Example Response
```json
{ 
   "access_token":"a959083fccacea34e1ecdc9acf4ab24b38c9aacd317f0c3bf9e1ae51b25a5a5b10b92174d4327c60024307605e5d927c1a4bca1da94040a76f6c12be6e85a8a9457d83039068",
   "token_type":"Bearer",
   "expires_in":3600,
   "scope":"identify email profile"
}
```

{% include links.html %}
