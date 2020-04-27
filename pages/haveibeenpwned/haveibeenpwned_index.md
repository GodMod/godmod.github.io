---
title: Have I been pwned
sidebar: sidebar10
permalink: haveibeenpwned_index.html
folder: haveibeenpwned
---

## Introduction

This extension checks the user passwords during login, registration and password change against the online service "Have I been pwned" to check if the password is already known from leaks in online services.

## License
[GMLv1](license.html)

## GDPR

The extension does _not_ transfer the password to the "Have I been pwned" service. In order to protect the value of the source password being searched for, "Have I been pwned" service implements a k-Anonymity model that allows a password to be searched for by partial hash. This allows the first 5 characters of a SHA-1 password hash to be passed to the API. On average, a range search returns 478 hash suffixes, although this number will differ depending on the hash prefix being searched for. The smallest result is 381, the largest 584. You can read more about [how k-Anonymity and the "Have I been pwned"  range search protects searched passwords](https://www.troyhunt.com/ive-just-launched-pwned-passwords-version-2).

Nevertheless, you should tell your users that their passwords are checked against the "Have I been pwned" service and link to their [Privacy Policy](https://haveibeenpwned.com/Privacy).

{% include links.html %}
