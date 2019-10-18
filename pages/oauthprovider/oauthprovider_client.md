---
title: User-API
sidebar: sidebar1
permalink: oauthprovider_client.html
folder: oauthprovider
---

## Add OAuth-Client
* Name - *the Name of your Client*
* Redirect-URL - *insert the redirect-URL of your application, where the user should be returned*
* Allow implicit Grant type - *should only enabled for JavaScript applications*
* Allow Password Grant type - *should only enabled for own applications, if the login with username and password is really required (e.g. at mobile application)*

## Edit OAuth-Client
When edit an OAuth-Client, you will get the following additional information:
* Authorization-URL - *Copy it into your application*
* Token-Endpoint - *Copy it into your application*
* User-API Endpoint - *Copy it into your application*
* Client-ID - *Copy it into your application*
* Client-Secret - *Copy it into your application, but it should be kept secret*
* JWT-Secret - *Used to verify the Signature of the JWT Token*

{% include links.html %}
