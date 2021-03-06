---
title: Generic OAuth Login
sidebar: sidebar3
permalink: genoauth_index.html
folder: genoauth
---

## Introduction

This extension allows the 3rd Party Login (like Facebook or Google) using an generic OAuth Provider.

## License
[GMLv1](license.html)

## OpenID-Connect (OIDC)
As OpenID-Connect uses the OAuth2 Protocol, this extension also works with OIDC-Server, like Keycloak etc. But as there is currently no autoconfiguration implemented, you have to extract the needed configuration from the `<domain.com>/.well-known/openid-configuration` file.

## Security
Please use only encrypted connections (SSL/TLS) for accessing the OAuth-Endpoints, as personal information (e.g. email address) is transfered or can be accessed.
Also, your WSC installation using the 3rd Party Login should only use an encrypted connection.

## Problems
Several clients have problems with the `index.php` in the WSC-URLs. Therefore your should configure the [SEO friendly URLs](https://www.woltlab.com/article/25-setting-up-user-friendly-urls/) to get rid of the `index.php`.


{% include links.html %}
