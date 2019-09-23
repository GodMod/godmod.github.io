---
title: Customization
sidebar: sidebar2
permalink: wscoauth_custom.html
folder: wscoauth
---

## Customize Button Colors

To change the color of the login/connect buttons, you can add the following SCSS to your style and adjust the colors:

```scss
.thirdPartyLogin {
  .thirdPartyLoginButton.wcfoauthLoginButton {
    background-color: rgba(33, 150, 243, 1);

    &:hover {
      background-color: rgba(26, 119, 201, 1);
    }
  }
}
```

## Customize Button Icon

You can replace the Icon at `<WSC-Folder>/images/wcf_oauth.png` with your own icon.

{% include links.html %}
