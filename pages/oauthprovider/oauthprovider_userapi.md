---
title: User-API
sidebar: sidebar1
permalink: oauthprovider_userapi.html
folder: oauthprovider
---

## Introduction

The User-API returns information about the current user, like username, email-address or profile information. This depends on the scope of the tokens.

## URL
You can get the URL for the User-API when editing the OAuth-Client.

## Authentication

The User-API requires authentication by using an Access Token. Also, an JWT Token can be used to access this API.

You can pass the Access/JWT Token using the `GET` or `POST` param `access_token`, but you should prefer using `POST` for security reasons.

```php
$request = new HTTPRequest('https://test.eqdkp-plus.eu/wcf/oauth-user/?access_token='.$data['access_token']);
$request->execute();
```

Or the token can be passed by using the HTTP Header `Authorization` like this:

```php
$request = new HTTPRequest('https://test.eqdkp-plus.eu/wcf/oauth-user/');
$request->addHeader('Authorization', 'Bearer '.$data['access_token']);
$request->execute();
```

## Request Format

The Request should be made using `GET`, but `POST` is also possible.
Except the `access_token` parameter, there are no other parameters.

## Example Request

Example request with Access Token:

```php
$request = new HTTPRequest('https://test.eqdkp-plus.eu/wcf/oauth-user/');
$request->addHeader('Authorization', 'Bearer 82ba1fa5bab8932a49a011c8f7004a17ee0b134c906ecf478804c79fc18ca6d2d72fd87c299f507370d2e054e79d9e887543');
$request->execute();
```

Example request with JWT Token:

```php
$request = new HTTPRequest('https://test.eqdkp-plus.eu/wcf/oauth-user/?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL3NvbnN0aWdlXC9mb3J1bTUuMS43XC91cGxvYWRcLyIsImF1ZCI6Imh0dHA6XC9cL2xvY2FsaG9zdFwvc29uc3RpZ2VcL2ZvcnVtNS4xLjdcL3VwbG9hZFwvIiwiaWF0IjoxNTY5MTYxNDI5LCJuYmYiOjE1NjkxNjEzNjksImV4cCI6MTU2OTE2MzIyOSwiZGF0YSI6eyJjbGllbnRJRCI6IjE0MjE1ODkxOTgiLCJzY29wZSI6ImlkZW50aWZ5IGVtYWlsIHByb2ZpbGUiLCJ1c2VySUQiOjEsInVzZXJuYW1lIjoicm9vdCIsImVtYWlsIjoiYWRtaW5AYWRtaW4uZGUifX0.8agUuQAqoqBRHo5wHJRQMtSJHmvNfVBd7s1eURdVHw8');
$request->execute();
```

## Response Format

The response has `JSON` format. The response only contains the fields corresponding to the scope of the tokens.

## Example Response

Example for scope `identify` / `openid`:

```json
{ 
   "sub":1,
   "userID":1,
   "name":"root",
   "username":"root",
   "preferred_username":"root",
   "picture":"data:image\/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNiAxNiIgd2lkdGg9IjEyOCIgaGVpZ2h0PSIxMjgiPjxwYXRoIGZpbGw9IiNkYzc2ZTkiIGQ9Ik0wIDBoMTZ2MTZIMHoiLz48dGV4dCB4PSI4IiB5PSI4IiBmaWxsPSIjZmZmIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBkeT0iLjNlbSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjciPlJPPC90ZXh0Pjwvc3ZnPg==",
   "picture_height":128,
   "picture_width":128
}
```

Example for scope `email`:

```json
{ 
   "email":"admin@admin.de",
   "email_verified": true
}
```


Example with all scopes (`identify` / `openid`, `email` and `profile`):

```json
{ 
   "sub":1,
   "userID":1,
   "name":"root",
   "username":"root",
   "preferred_username":"root",
   "picture":"data:image\/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNiAxNiIgd2lkdGg9IjEyOCIgaGVpZ2h0PSIxMjgiPjxwYXRoIGZpbGw9IiNkYzc2ZTkiIGQ9Ik0wIDBoMTZ2MTZIMHoiLz48dGV4dCB4PSI4IiB5PSI4IiBmaWxsPSIjZmZmIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBkeT0iLjNlbSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjciPlJPPC90ZXh0Pjwvc3ZnPg==",
   "picture_height":128,
   "picture_width":128,
   "email":"admin@admin.de",
   "profile":{ 
      "userOption1":null,
      "userOption2":"0000-00-00",
      "userOption3":1,
      "userOption4":"0",
      "userOption5":null,
      "userOption6":null,
      "userOption7":null,
      "userOption8":null,
      "userOption9":null,
      "userOption10":null,
      "userOption11":null,
      "userOption12":null,
      "userOption13":null,
      "userOption14":null,
      "userOption15":1,
      "userOption16":null,
      "userOption17":1,
      "userOption18":1,
      "userOption19":"0",
      "userOption20":"0",
      "userOption21":"0",
      "userOption22":"3",
      "userOption23":"1",
      "userOption24":1,
      "userOption25":"1",
      "userOption26":"0",
      "userOption27":"0",
      "userOption28":"0",
      "userOption29":"0",
      "userOption30":"0",
      "userOption31":1,
      "userOption35":"0",
      "userOption36":"0",
      "userOption37":0,
      "userOption39":null,
      "groupID":4,
      "cssClassName":"blue",
      "registrationDate":1549550181,
      "banned":0,
      "banReason":null,
      "banExpires":0,
      "oldUsername":"",
      "birthday":"",
      "age":0,
      "rank":{ 

      },
      "title":"root",
      "userTitle":"Administrator",
      "signature":""
   },
   "groups":{
	"1":"Jeder",
	"3":"Registrierte Benutzer",
	"4":"Administratoren
   "},
   "locale":"de-DE",
   "zoneinfo":"Europe\/Berlin",
   "gender":"male"
}
```


{% include links.html %}
