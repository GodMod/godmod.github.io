---
title: Logout-Endpoint
sidebar: sidebar1
permalink: oauthprovider_logout.html
folder: oauthprovider
---

## Introduction

The Logout-Endpoint logs the user out of the WSC.

## URL

The URL is `https://somedomain.com/index.php?oauth-logout` or `https://somedomain.com/oauth-logout/`.

## Request Format

The following parameters are optional:

| Name | Description |
|------|-------------|
|`post_logout_redirect_uri` | The URL where the user should be redirected to after Logout. Most match with the Redirect-URIs of the Client. |
|`id_token_hint` | Recommended. An JWT Token, which is used to terminate all existing sessions with the Client. |
|`state` | a custom state from your application. Please see next chapter for using this param for security purposes |

## State and Security

The `state` param can be used to prevent CSRF and Clickjacking vulnerabilities. 
`state` is sent in the authorization request and returned back in the response and should be a value that binds the user's request to their authenticated `state`. For example, state could be a hash of the user's session cookie, or some other nonce that can be linked to the user's session.
When a user begins an authorization flow on the client, a `state` is generated that is unique to that user's request. This value is stored somewhere only accessible to the client and the user, i.e. protected by the same-origin policy. When the user is redirected, the `state` parameter is returned. The client validates the request by checking that the `state` returned matches the stored value. If they match, it is a valid authorization request. If they do not match, it's possible that someone intercepted the request or otherwise falsely authorized themselves to another user's resources, and the request should be denied.
While the use of the `state` parameter is not required, it is highly recommend that you implement it for the security of your own applications and data.

## Example Request

```php
https://somedomain.com/oauth-logout/?id_token_hint=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3RcL3NvbnN0aWdlXC9mb3J1bTUuMS43XC91cGxvYWRcLyIsImF1ZCI6Imh0dHA6XC9cL2xvY2FsaG9zdFwvc29uc3RpZ2VcL2ZvcnVtNS4xLjdcL3VwbG9hZFwvIiwiaWF0IjoxNTY5MTYxNDI5LCJuYmYiOjE1NjkxNjEzNjksImV4cCI6MTU2OTE2MzIyOSwiZGF0YSI6eyJjbGllbnRJRCI6IjE0MjE1ODkxOTgiLCJzY29wZSI6ImlkZW50aWZ5IGVtYWlsIHByb2ZpbGUiLCJ1c2VySUQiOjEsInVzZXJuYW1lIjoicm9vdCIsImVtYWlsIjoiYWRtaW5AYWRtaW4uZGUifX0.8agUuQAqoqBRHo5wHJRQMtSJHmvNfVBd7s1eURdVHw8&state=d927c1a4bca1da94040&post_logout_redirect_uri=https://somedomain.com/post-logout.html
```

## Response Format

The user will be redirected to the given `post_logout_redirect_uri`. The `state` will be included, if given at the request.
```php
https://somedomain.com/post-logout.html?state=d927c1a4bca1da94040
```
{% include links.html %}
