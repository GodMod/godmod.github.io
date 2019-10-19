---
title: Customization
sidebar: sidebar8
permalink: dices_custom.html
folder: dices
---

## Customize Button Colors

To change the color of the dices, you can add the following SCSS to your style and adjust the colors:

```scss
div[data-dice-id='0']:before, .redactor-box .re-dice .fa-cube {
   color: #000000;
}

div[data-dice-id='1']:before, .redactor-box .re-dice1 .fa-cube {
   color: #ff0000;
}

div[data-dice-id='2']:before, .redactor-box .re-dice2 .fa-cube {
   color: #c217ff;
}

div[data-dice-id='3']:before, .redactor-box .re-dice3 .fa-cube {
   color: #2aff00;
}

```


{% include links.html %}
