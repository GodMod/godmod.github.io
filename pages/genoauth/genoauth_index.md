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

## Security
Please use only encrypted connections (SSL/TLS) for accessing the OAuth-Endpoints, as personal information (e.g. email address) is transfered or can be accessed.
Also, your WSC installation using the 3rd Party Login should only use an encrypted connection.

## Problems
Several clients have problems with the `index.php` in the WSC-URLs. Therefore your should configure the [SEO friendly URLs](https://www.woltlab.com/article/25-setting-up-user-friendly-urls/) to get rid of the `index.php`.


{% include links.html %}
