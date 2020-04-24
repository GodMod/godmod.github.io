---
title: User-API Settings
sidebar: sidebar3
permalink: genoauth_settingsuserapi.html
folder: genoauth
---

## User-API Settings

### General
* URL of the User-API - *Where user data like Username, ID and Email address can be retrived. Only JSON APIs are supported.*
* Passing of the Access-Tokens - *How the access token should be passed. Some applications allow passing as a param, or using the Authorization Header*
* Parametername of the Access-Tokens - *Name of the param which should contain the access token*
* Fast Usercreation during the Login - *Instead of redirecting the user to the register form, it is tried to create the user during the login process.*
* User can remove the connection with the OAuth/OIDC-Account - *If the user should always use the connected OAuth/OIDC-Account, you should disallow removing the connection with connected OAuth/OIDC-Account*

### Required Parameternames
These Parameternames can be retrieved from the documentation of the Oauth-Provider, and are required for successfully creating and authentication of an user. If an OIDC-Provider is used, use the Discovery Feature to help you filling out these values.

* Key of the User-ID - *Insert which key in the response contains the User-ID. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`. Common used values are `sub` and `id`.*
* Key of the Username - *Insert which key in the response contains the username. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`. Common used values are `name`, `preferred_username` and `username`.*
* Key of the Email-Address - *Insert which key in the response contains the email address. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`. A common used value is `email`.*

### Additional Parameternames
These Parameternames are not required, but can help in creating new users, as they will fill out some settings for the User.
* Key of the Locale - *Insert which key in the response contains the Locale. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`. Leave empty if there is no support for the Locale in the User-API. A common used value is `locale`. *
* Key of the Timezone - *Insert which key in the response contains the Timezone. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`. Leave empty if there is no support for the Timezone in the User-API. A common used value is `zoneinfo`.*

### Usergroups
It is possible to sync usergroups, if the User-API provides role/group information as an Array.

* Key of the roles array - *Insert which key in the response contains the roles/groups array. Nested Indices can be used by seperating the keys with colons. E.g. for accessing `$userData['firstKey']['secondKey']` insert `firstKey:secondKey`. Leave empty if there is no support for the roles/groups in the User-API.*
* Mapping of the OIDC provider’s roles to WoltLab usergroups - *Here you can assign a value of the OIDC provider’s roles array to the ID of a WoltLab usergroup. So if the roles array contains the values `admin`, and you have a corresponding administrator-group with the ID 4, you can create a mapping `admin=4`, so users with role `admin` are assigned to WoltLab group with ID 4 during account creation and login (if enabled). Create one mapping per line.*
* Sync Usergroups during login - *During the login, the usergroups from the roles array are assigned to the users. This will also remove the user from other WoltLab groups, therefore create a mapping of the groups for all your roles from the OIDC provider.*


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
* Key of the Locale - `locale`
* Key of the Timezone - `zoneinfo`


{% include links.html %}
