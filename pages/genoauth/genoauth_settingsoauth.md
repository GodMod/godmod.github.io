---
title: OAuth Settings
sidebar: sidebar3
permalink: genoauth_settingsoauth.html
folder: genoauth
---

## OAuth Settings

* Name of the OAuth Provider - *The Name will be shown on Login and Connect Button*
* Client-ID - *The Client-ID of your application that you have registered at the OAuth-Provider*
* Client Secret - *The Client Secret of your application that you have registered at the OAuth-Provider*
* Scope - *The Scope(s) required for the OAuth-Provider. Multiple can be added seperated by space. Choose a scope that will include the user's email address*
* OIDC Discovery URL - *If OIDC is supported by your provider, insert here the URL of your OIDC-Provider, or directly the URL to a OpenID Discovery file, which is normally available at "https://somedomain.com/.well-known/openid-configuration". After inserting, click on the Button "Search settings" and some fields will be filled out.*
* Authorization Endpoint - *URL for the Authorization Endpoint of the OAuth-Provider*
* Token Endpoint - *URL for the Token Endpoint of the OAuth-Provider*
* Passing of the Client-Credentials to the Token-Endpoint - *How the Client-Credentials should be passed to the Token-Endpoint. Select between "Post-Parameter" and "Authorization-Header Basic"*

## Example - Discord
As an example, the plugin will be configured for using [Discord](https://discordapp.com). All required information can be found at the [Developer Portal](https://discordapp.com/developers/docs/topics/oauth2).

* Name of the OAuth Provider - `Discord`
* Client-ID - `1234567890`
* Client Secret - `AbCdEfGhiJAbCdEfGhiJAbCdEfGhiJ`
* Scope - `identify email`
* Authorization Endpoint - `https://discordapp.com/api/oauth2/authorize`
* Token Endpoint - `https://discordapp.com/api/oauth2/token`
* Passing of the Client-Credentials to the Token-Endpoint - `Post-Parameter`

## Example - Nextcloud
For Nextcloud, the [SEO friendly URLs](https://www.woltlab.com/article/25-setting-up-user-friendly-urls/) must be configured.

* Name of the OAuth Provider - `Nextcloud`
* Client-ID - `1234567890`
* Client Secret - `AbCdEfGhiJAbCdEfGhiJAbCdEfGhiJ`
* Scope - `email`
* Authorization Endpoint - `https://cloud.somedomain.com/index.php/apps/oauth2/authorize`
* Token Endpoint - `https://cloud.somedomain.com/index.php/apps/oauth2/api/v1/token`
* Passing of the Client-Credentials to the Token-Endpoint - `Post-Parameter`

## Example - Keycloak
You will find the Endpoint-URLs and available scopes at the configuration file `https://somedomain.com/auth/realms/{realm-name}/.well-known/openid-configuration`.

* Name of the OAuth Provider - `Keycloak`
* Client-ID - `1234567890`
* Client Secret - `AbCdEfGhiJAbCdEfGhiJAbCdEfGhiJ`
* Scope - `email openid`
* OIDC Discovery URL - `https://somedomain.com/realms/{realm-name}/.well-known/openid-configuration`
* Authorization Endpoint - `https://somedomain.com/realms/{realm-name}/protocol/openid-connect/auth`
* Token Endpoint - `https://somedomain.com/realms/{realm-name}/protocol/openid-connect/token`
* Passing of the Client-Credentials to the Token-Endpoint - `Authorization-Header Basic`

{% include links.html %}
