---
title: WSC OAuth-Provider
sidebar: sidebar1
permalink: oauthprovider_index.html
folder: oauthprovider
---

## Introduction

The WSC OAuth-Provider allows your WSC installation to be an OAuth-Provider. Therefore other applications supporting OAuth can use your WSC installation for authentication of the users.

## Permissions

There are two group permissions:

| Name | Type | Description |
|------|------|-------------|
| Can use OAuth | User | Allows an user to authorize applications |
| Can manage OAuth-Clients | Admin | Can manage OAuth-Clients |

## Settings
`Configuration > Security > OAuth-Provider`:
* Send Emails to the user if client is authorized for the first time - *user get's an email with information about his authorization. You should enable this option e.g. when using password grant type.*

## Security
Please use only encrypted connections (SSL/TLS) for accessing the OAuth-Endpoints, as personal information (e.g. email address) is transfered or can be accessed.
Also, use `POST` for transfering parameters wherever possible.

## License
AGPLv3 - See [https://eqdkp-plus.eu/en/about/license-agpl.html](https://eqdkp-plus.eu/en/about/license-agpl.html)


{% include links.html %}
