---
title: User-API Settings
sidebar: sidebar3
permalink: genoauth_settingsuserapi.html
folder: genoauth
---

## User-API Settings

* URL of the User-API - *Where user data like Username, ID and Email address can be retrived. Only JSON APIs are supported.*
* Passing of the Access-Tokens - *How the access token should be passed. Some applications allow passing as a param, or using the Authorization Header*
* Parametername of the Access-Tokens - *Name of the param which should contain the access token*
* Key of the User-ID - *Insert which key in the response contains the User-ID. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`*
* Key of the Username - *Insert which key in the response contains the username. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`*
* Key of the Email-Address - *Insert which key in the response contains the email address. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`*
* Fast Usercreation during the Login - *Instead of redirecting the user to the register form, it is tried to create the user during the login process.*


## Example - Discord
As an example, the plugin will be configured for using [Discord](https://discordapp.com). All required information can be found at the [Developer Portal](https://discordapp.com/developers/docs/resources/user#get-current-user).

* URL of the User-API - `https://discordapp.com/api/users/@me`
* Passing of the Access-Tokens - `Authorization-Header "Bearer"`
* Parametername of the Access-Tokens - `access_token`
* Key of the User-ID - `id`
* Key of the Username - `username`
* Key of the Email-Address - `email`

## Example - Nextcloud
For Nextcloud, the [SEO friendly URLs](https://www.woltlab.com/article/25-setting-up-user-friendly-urls/) must be configured.

* URL of the User-API - `https://cloud.somedomain.com/ocs/v2.php/cloud/user?format=json`
* Passing of the Access-Tokens - `Authorization-Header "Bearer"`
* Parametername of the Access-Tokens - `access_token`
* Key of the User-ID - `ocs:data:id`
* Key of the Username - `ocs:data:display-name`
* Key of the Email-Address - `ocs:data:email`

## Example - Keycloak
You will find the Endpoint-URLs and available scopes at the configuration file `https://somedomain.com/auth/realms/{realm-name}/.well-known/openid-configuration`.

* URL of the User-API - `https://somedomain.com/realms/{realm-name}/protocol/openid-connect/userinfo`
* Passing of the Access-Tokens - `Authorization-Header "Bearer"`
* Parametername of the Access-Tokens - `access_token`
* Key of the User-ID - `sub`
* Key of the Username - `name` or `preferred_username`
* Key of the Email-Address - `email`

{% include links.html %}
