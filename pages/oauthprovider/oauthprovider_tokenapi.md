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



### Example Request

```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-token/', array(
	'client_id' => '1421589198', 
	'client_secret' => 'C7LxkuPm0a7JozCd16cyiKLA31UHqbwdUZPxX8auDDO3uiiFqa1Q7SRObHtLsd2k9pmYZqmAqKBlkf3ThCtScMSTzhz9DSfjW7GP0DAfNaWO0ZXNT8SzNqWO6yTfwVq7', 
	'grant_type' => 'authorization_code', 
	'code' => 'aa7c87e3595cc9ae1f04a4cf7769a8ccb972b99931a542e2aedecd9428aa7d8c18d6f16b2fa96020b4cf5aff44d8ce87bdec',
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

If `openid` is in the scope, and additional JWT-/ID-Token is passed to the output:

```json
{ 
   "access_token":"a959083fccacea34e1ecdc9acf4ab24b38c9aacd317f0c3bf9e1ae51b25a5a5b10b92174d4327c60024307605e5d927c1a4bca1da94040a76f6c12be6e85a8a9457d83039068",
   "token_type":"Bearer",
   "expires_in":3600,
   "scope":"identify email profile",	"id_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL3NvbnN0aWdlXC9mb3J1bTUuMS43XC91cGxvYWRcLyIsImF1ZCI6IjEzMDc3MzQwMDgiLCJpYXQiOjE1NzE1NTU4MzgsIm5iZiI6MTU3MTU1NTc3OCwiZXhwIjoxNTcxNTU5NDM4LCJzdWIiOjEsIm5hbWUiOiJyb290Iiwibm9uY2UiOiJjYzA1OGYyMGNiNzU5ZTI4NTQzYjJmZjEzOTlhMGI2ZiIsInNjb3BlIjoib3BlbmlkIGVtYWlsIiwiZW1haWwiOiJhZG1pbkBhZG1pbi5kZSJ9.R25eS35w-qbvCMZjr9yBFC2cMXEVnhTWFiRjCh2zS4w"
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

If `openid` is in the scope, and additional JWT-/ID-Token is passed to the output:

```json
{ 
   "access_token":"a959083fccacea34e1ecdc9acf4ab24b38c9aacd317f0c3bf9e1ae51b25a5a5b10b92174d4327c60024307605e5d927c1a4bca1da94040a76f6c12be6e85a8a9457d83039068",
   "token_type":"Bearer",
   "expires_in":3600,
   "scope":"identify email profile",	"id_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL3NvbnN0aWdlXC9mb3J1bTUuMS43XC91cGxvYWRcLyIsImF1ZCI6IjEzMDc3MzQwMDgiLCJpYXQiOjE1NzE1NTU4MzgsIm5iZiI6MTU3MTU1NTc3OCwiZXhwIjoxNTcxNTU5NDM4LCJzdWIiOjEsIm5hbWUiOiJyb290Iiwibm9uY2UiOiJjYzA1OGYyMGNiNzU5ZTI4NTQzYjJmZjEzOTlhMGI2ZiIsInNjb3BlIjoib3BlbmlkIGVtYWlsIiwiZW1haWwiOiJhZG1pbkBhZG1pbi5kZSJ9.R25eS35w-qbvCMZjr9yBFC2cMXEVnhTWFiRjCh2zS4w"
}
```

## Password Grant Type
This grant type allows exchanging supplied user credentials for an access token.

### Request Format

Only `POST` requests should be used for accessing this endpoint. Also, this endpoint accepts a content type of `application/x-www-form-urlencoded` only.

The following parameters are required:

| Name | Description |
|------|-------------|
|`client_id` | your application's client id |
|`grant_type` | must be set to `password` |
|`username` | user's username |
|`password` | user's password |

The following parameters are optional:

| Name | Description |
|------|-------------|
|`scope` | the scopes you want to request, space-delimited; default: `identify` |
|`nonce` | a custom random value from your application, which will be included in an ID Token (if `openid` scope is requested) |

### Example Request
```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-token/', array(
	'client_id' => '1421589198', 
	'grant_type' => 'password', 
	'username' => 'Hillary', 
	'password' => '12345678'), "application/x-www-form-urlencoded; charset=utf-8");
```

Example request with scopes:

```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-token/', array(
	'client_id' => '1421589198', 
	'grant_type' => 'password', 
	'username' => 'Hillary',
	'scope' => 'openid email profile',
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
   "scope":"identify"
}
```

Example response with scopes:

```json
{ 
   "access_token":"0c8cebbe7d06085697b6e1237ca8abd222e2aac3e1aa4f10366ddfe1cde7c657ba21ceeb548754aa1b08d5e1c6c94a1c0e786993b4e333d5122a031b7348fe3425119a0b9b03",
   "token_type":"Bearer",
   "refresh_token":"82cd7660c157115cc0bfc6e69c7f515f82f1e6f3f0336de7ced915ad6376e24b6a190aab64a5357da69cc7ea265df2bae4cc2804939dcb5ffd7abb73381e263a8ff7a2c23e17",
   "expires_in":3600,
   "scope":"openid email profile",
   "id_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL3NvbnN0aWdlXC9mb3J1bTUuMS43XC91cGxvYWRcLyIsImF1ZCI6IjEzMDc3MzQwMDgiLCJpYXQiOjE1NzE1NTk4MTIsIm5iZiI6MTU3MTU1OTc1MiwiZXhwIjoxNTcxNTYzNDEyLCJzdWIiOjEsIm5hbWUiOiJyb290Iiwibm9uY2UiOiIiLCJzY29wZSI6Im9wZW5pZCBlbWFpbCBwcm9maWxlIiwiZW1haWwiOiJhZG1pbkBhZG1pbi5kZSJ9.zr6duC34thO0rmP0g5NwRBM61AJDCiURu0dLAuHxUzg"
}
```

{% include links.html %}
