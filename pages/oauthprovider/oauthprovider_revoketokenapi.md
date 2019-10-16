---
title: Revoke Token-Endpoint
sidebar: sidebar1
permalink: oauthprovider_revoketokenapi.html
folder: oauthprovider
---

## Introduction

The Revoke Token API deletes an existing access and/or refresh token.

## URL

The URL is `https://somedomain.com/index.php?oauth-revoketoken` or `https://somedomain.com/oauth-revoketoken/`.

## Request Format

Only `POST` requests should be used for accessing this endpoint. Also, this endpoint accepts a content type of `application/x-www-form-urlencoded` only.

The following parameters are required:

| Name | Description |
|------|-------------|
|`access_token` | the access token you want to delete |


## Example Request

```php
$strResult = $this->urlfetcher->post('https://test.eqdkp-plus.eu/wcf/oauth-revoketoken/', array(
	'access_token' => 'aa7c87e3595cc9ae1f04a4cf7769a8ccb972b99931a542e2aedecd9428aa7d8c18d6f16b2fa96020b4cf5aff44d8ce87bdec', 
), "application/x-www-form-urlencoded; charset=utf-8");
```

## Response Format

The response header is always `200 OK`, without a body.


{% include links.html %}
