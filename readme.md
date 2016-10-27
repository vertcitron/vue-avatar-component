# vue-avatar-component

This vue.js component provide a simple way to generate rounded and colored avatar stickers to use in your applications.

If you just provide a name to the component, i will show a colored patch showing the provided name's initials. Its color is depending and is unique for each given name.

If you provide an image url, this image will be shown, sized and truncated to fit into the component's placeholder.

### Usage

1. require the component : `import Avatar from 'vue-avatar-component'`
2. register the component from the component where you want to use it :   `component: { Avatar }`
3. place it in your template, with the attributes you need :   `<avatar fullname="Foo Bar"></avatar>` (for example)

### Parameters

`fullname` :   the full name from which the initials and the color will be computed. Initials are extracted taking the first letter of each word, separated by a space or an hyphen. If there is more, only the 3 first initials are kept. For example, `Foo Bar` gives `FB`, `My Foo-Bar` gives `MFB`, `FOO` gives `F` and `My Fantastic Vue Component` gives `MFV`. If not provided, fullname defaults to '##'.

`size` : the size of the sticker to generate, in pixels. Provide it as a binding to pass a number and not a litteral string (`<avatar :size="36"></avatar>`). If not provided, the size defaults to 48 pixels. The font size inside the avatar is computed from its overall size (half if 1 or 2 letters, third for 3 letters).

`image` : the url of the image to fit in the avatar sticker. If provided not empty, initials will not show and the image wil be shown.

`radius` : percentage of the overall size to show the rounded corners of the avatar. Provide a number beetween 0 and 50 : at 0%, the avatar will be a square, at 50% it will be exactly circular. This pecentage defaults to 50 if not provide. Provide a binded number as for the size parameter.

`color` : If provided, overides the computed color for the initials based avatar. Just provide a CSS color (named, hex or rgba fit).

### examples

<table>
  <tr>
    <td><code>&lt;avatar fullname="My Fabulous Component"&gt;&lt;/avatar&gt;</code> will show :</td>
    <td> <img src="https://github.com/ssouron/vue-avatar-component/blob/master/img/example1.jpg" /> </td>
  </tr>
  <tr>
    <td> <code>&lt;avatar fullname="Foo Bar" size="60"&gt;&lt;/avatar&gt;</code> will show : </td>
    <td> <img src="https://github.com/ssouron/vue-avatar-component/blob/master/img/example2.jpg" /> </td>
  </tr>
  <tr>
    <td> <code>&lt;avatar image="http://lorempicsum.com/simpsons/255/200/9" size="96"&gt;&lt;/avatar&gt;</code> will show : </td>
    <td> <img src="https://github.com/ssouron/vue-avatar-component/blob/master/img/example3.jpg" /> </td>
  </tr>
  <tr>
    <td> <code>&lt;avatar image="http://lorempicsum.com/simpsons/255/200/5" size="96" radius="0"&gt;&lt;/avatar&gt;</code> will show : </td>
    <td> <img src="https://github.com/ssouron/vue-avatar-component/blob/master/img/example4.jpg" /> </td>
  </tr>
  <tr>
    <td> <code>&lt;avatar fullname="Foo Bar" radius="25" color="red"&gt;&lt;/avatar&gt;</code> will show : </td>
    <td> <img src="https://github.com/ssouron/vue-avatar-component/blob/master/img/example5.jpg" /> </td>
  </tr>
</table>

