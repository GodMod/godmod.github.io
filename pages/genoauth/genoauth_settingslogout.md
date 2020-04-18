---
title: Logout Settings
sidebar: sidebar3
permalink: genoauth_settingslogout.html
folder: genoauth
---

## Logout Settings

* Redirect the User after the Logout - *Users are redirected after logout, e.g. for calling an Logout-URL at the Authorization-Server. Only Users that have an connected OAuth-Account will be redirected.*
* Logout Redirect-URL - *Insert a complete and valid URL where the user should be redirected to after Logout. Only users that have an connected OAuth-Account will be redirected.*


## Example - Keycloak
You will find the Endpoint-URLs and available scopes at the configuration file `https://somedomain.com/auth/realms/{realm-name}/.well-known/openid-configuration`.

* Redirect the User after the Logout - `Yes`
* Logout Redirect-URL - `https://somedomain.com/auth/realms/{realm-name}/protocol/openid-connect/logout?redirect_uri=http%3A%2F%2Fyour-forum.com`

{% include links.html %}
