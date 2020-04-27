---
title: Have I been pwned - Settings
sidebar: sidebar10
permalink: haveibeenpwned_settings.html
folder: haveibeenpwned
---

## Extension Settings
You will find the extension settings at `Configuration > Security > Passwords`.
* Add user with leaked password into a user group - *Enable this option if you want that users with a leaked password should be added to a configured group. You can use this to remove permissions from users with a weak password. After they have choosen a new and secure password, they are removed from the choosen group. As they are only added to the group, they will remain in their current groups, therefore you should use the "Never" setting of permissions in your newly created group to deny access to the choosen actions.* 
* User group where users with leaked passwords are added to - *Choose the group(s) users with a leaked password should be added to.*

## Group Permissions
You will find the group permissions at `User Permissions > Passwords`.
* Check Passwords if they are known from leaks - *This is enabled for all groups by default. Every time a user login occurs or they change their password, the password is checked if it is known from leaks.*
* Can use leaked passwords - *This is disabled for all groups by default. If enabled, an user get's an hint during login that his password is known, but he is not enforced to change it and can still use all features from your site.*


{% include links.html %}
