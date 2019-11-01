---
title: How it works
sidebar: sidebar1
permalink: oauthprovider_howitworks.html
folder: oauthprovider
---

## How it works

![alt text](howitworks.jpg "")

* You install OAuth Provider extension into a WSC installation. This will be your "Master" system, where your user will register their accounts, authorize Clients etc. As the OAuth Provider does not change the login, users can still use Security features like Two-Factor Authentication etc. for Login at the "Master" system.

* You setup your other Clients (another WSC installation, Gitea, Jira, Own Website, ...) and configure them 

* When User "John" wants to login at a Client, he clicks on the Login-Button
* "John" is redirected to the OAuth Provider and must login there
* "John" must authorize the Client
* "John" is redirected back to the Client where he wants to login
* The Client now logs John in and creates an account for John if neccessary

{% include links.html %}
