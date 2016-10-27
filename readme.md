# vue-avatar-component

This vue.js component provide a simple way to generate rounded and colored avatar stickers to use in your applications.

If you just provide a name to the component, i will show a colored patch showing the provided name's initials. Its color is depending and is unique for each given name.

If you provide an image url, this image will be shown, sized and truncated to fit into the component's placeholder.

### Installation

`npm install --save-dev vue-avatar-component`

### Example Usage from within a .vue component

```javascript
<template>
  <div>
    <avatar fullname="My Sticker" size="96"></avatar>
  </div>
</template>

<script>
  import Avatar from 'vue-avatar-component'
  export default {
    components: { Avatar }
  }
</script>
```

This will show this avatar as result :

![avatar](https://raw.githubusercontent.com/ssouron/vue-avatar-component/master/img/example0.jpg)

### Parameters

`fullname` :   the full name from which the initials and the color will be computed. Initials are extracted taking the first letter of each word, separated by a space or an hyphen. If there is more, only the 3 first initials are kept. For example, `Foo Bar` gives `FB`, `My Foo-Bar` gives `MFB`, `FOO` gives `F` and `My Fantastic Vue Component` gives `MFV`. If not provided, fullname defaults to '##'.

`size` : the size of the sticker to generate, in pixels. If not provided, the size defaults to 48 pixels. The font size inside the avatar is computed from its overall size (half if 1 or 2 letters, third for 3 letters).

`image` : the url of the image to fit in the avatar sticker. If provided not empty, initials will not show and the image wil be shown. Be careful that if the provided image url is wrong, the component has its size but shows nothing.

`radius` : percentage of the overall size to show the rounded corners of the avatar. Provide a number beetween 0 and 50 : at 0%, the avatar will be a square, at 50% it will be exactly circular. This percentage defaults to 50 if not provided.

`color` : If provided, overides the computed color for the initials based avatar. Just provide a CSS color (named, hex or rgba fits).

### examples

If images don't show, go to this component's [github repository](https://github.com/ssouron/vue-avatar-component) to see the full README.

<table>
  <tr>
    <td><code>&lt;avatar fullname="My Fabulous Component"&gt;&lt;/avatar&gt;</code> will show :</td>
    <td> <img src="https://raw.githubusercontent.com/ssouron/vue-avatar-component/master/img/example1.jpg" /> </td>
  </tr>
  <tr>
    <td> <code>&lt;avatar fullname="Foo Bar" size="60"&gt;&lt;/avatar&gt;</code> will show : </td>
    <td> <img src="https://raw.githubusercontent.com/ssouron/vue-avatar-component/master/img/example2.jpg" /> </td>
  </tr>
  <tr>
    <td> <code>&lt;avatar image="http://lorempicsum.com/simpsons/255/200/9" size="96"&gt;&lt;/avatar&gt;</code> will show : </td>
    <td> <img src="https://raw.githubusercontent.com/ssouron/vue-avatar-component/master/img/example3.jpg" /> </td>
  </tr>
  <tr>
    <td> <code>&lt;avatar image="http://lorempicsum.com/simpsons/255/200/5" size="96" radius="0"&gt;&lt;/avatar&gt;</code> will show : </td>
    <td> <img src="https://raw.githubusercontent.com/ssouron/vue-avatar-component/master/img/example4.jpg" /> </td>
  </tr>
  <tr>
    <td> <code>&lt;avatar fullname="Foo Bar" radius="25" color="red"&gt;&lt;/avatar&gt;</code> will show : </td>
    <td> <img src="https://raw.githubusercontent.com/ssouron/vue-avatar-component/master/img/example5.jpg" /> </td>
  </tr>
</table>

### License

This Vue.js component is licensed under MIT License :

*Copyright © 2016, Stéphane Souron*

*Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:*

*The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.*

*The Software is provided “as is”, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the Software.
Except as contained in this notice, the name of the Stéphane Souron shall not be used in advertising or otherwise to promote the sale, use or other dealings in this Software without prior written authorization from Stéphane Souron.*


