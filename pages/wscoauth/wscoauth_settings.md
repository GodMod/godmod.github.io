---
title: Settings
sidebar: sidebar2
permalink: wscoauth_settings.html
folder: wscoauth
---

### General

* Name of the WSC OAuth-Provider - *The Name will be shown on the Login and Connect Button*
* Client-ID - *Copy the Client ID from your OAuth-Client of your WSC OAuth-Provider* 
* Client Secret - *Copy the Client Secret from your OAuth-Client of your WSC OAuth-Provider* 
* Authorization-URL of the OAuth-Provider - *Insert here the Authorization-URL of your WSC OAuth-Provider. The extension needs this for redirecting to the right OAuth-Provider.*

### User

* Fast Usercreation during the Login - *Instead of redirecting the user to the register form, it is tried to create the user during the login process.*
* Redirect User after Logout to the WSC OAuth-Provider Logout-Form - *If enabled, users with an connected WSC OAuth Account will be redirected after logout to the WSC OAuth-Provider Logout-Form, so they can also logout from the WSC OAuth-Provider.*
* User can remove the connection with the WSC OAuth Account - *If the user should always use the connected WSC OAuth-Provider, you should disallow removing the connection with connected WSC OAuth Account*

### Usergroups
It is possible to sync usergroups, if the User-API provides role/group information as an Array.

* Mapping of the WSC OAuth-Provider’s roles to WoltLab usergroups - *Here you can assign the name of the WSC OAuth-Provider’s group to the ID of a WoltLab usergroup. So if the roles array contains a group named `Administrator`, and you have a corresponding administrator-group with the ID 4, you can create a mapping `Administrator=4`, so users withhin group `Administrator` of the WSC OAuth-Provider are assigned to WoltLab group with ID 4 during account creation and login (if enabled). Create one mapping per line.*
* Sync Usergroups during login - *During the login, the usergroups from the roles array are assigned to the users. This will also remove the user from other WoltLab groups, therefore create a mapping of the groups for all your roles from the WSC OAuth-Provider.*

{% include links.html %}
