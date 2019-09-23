---
title: Customize
sidebar: sidebar3
permalink: genoauth_settingscustom.html
folder: genoauth
---

## Customize Button Colors

To change the color of the login/connect buttons, you can add the following SCSS to your style and adjust the colors:

```
.thirdPartyLogin {
  .thirdPartyLoginButton.genoauthLoginButton {
    background-color: rgba(33, 150, 243, 1);

    &:hover {
      background-color: rgba(26, 119, 201, 1);
    }
  }
}
```

## Customize Button Icon

To add a custom image to the Button, you can use the following CSS code. Please adjust the URL to your Icon and insert an absolute URL.
```
.thirdPartyLoginButton.genoauthLoginButton .icon {
   background: url(https://eqdkp-plus.eu/images/some_icon.png) no-repeat center center;
   background-size: contain;
}

```

{% include links.html %}
