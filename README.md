embedo [![npm version](https://badge.fury.io/js/embedo.svg)](https://badge.fury.io/js/embedo)
=============

<img align="right" width="100" height="100"
     title="Embedo"
     src="https://s16.postimg.org/5aauaeih1/embed.png" style="margin-right: 20px;">

Embedo is a simple, fast, lightweight and standalone library which lets you embed third-party content without any setup for oembed or SDK's. It also automagically organise the embeded container at almost any size, which makes it responsive friendly as well.

## Install

```sh
# npm Module
$ npm install embedo --save

# Bower
$ bower install embedo
```

### Import

Embedo CDN is also available under following link. The versions can be replaced according to your need, and ideally it should be hooked to `<body>` tag of your markup.

```html
<script src="https://cdn.jsdelivr.net/embedo/0.2.2/embedo.min.js"></script>
```

## Usage

Embedo supports AMD and CommonJS modules. Also, an example can be [found here](https://github.com/shobhitsharma/embedo/tree/master/example).

```js
const Embedo = require('embedo'); // OR import Embedo from 'embedo';
const embedo = new Embedo(); // OR const embedo = new Embedo();

embedo.load(<HTMLElement[object]>, <URL[string]>, <options[object]>);
```

Embedo automatically injects third-part social media SDKs once you include this to your project.

### Initialize Options

The following options can be set during library import is called:

| Parameter       | Type     | Default    | Description                                    |
| -------------   |----------|------------|------------------------------------------------|
| `facebook`      | number   | true      | Injects Facebook SDK                            |
| `twitter`       | number   | true      | Injects Twitter SDK                             |
| `instagram`     | boolean  | true      | Injects Instagram SDK                           |
| `youtube`       | boolean  | n/a       | Injects YouTube oEmbed                          |
| `pinterest`     | boolean  | false     | Injects Pinterest SDK                           |

## Events

### .load()

The `.load()` function is all what you need to embed third party content.
There is an **automagic** function which translates the embedded content to fit and centerize the parent container if `width` or `height` is provided. 
If `strict: true` option is passed, then it will be ignored.

```js
embedo.load(<HTMLElement>, <URL|string>, <options|{}>)
```

| Parameter       | Type     | Default    | Description                                    |
| -------------   |----------|------------|------------------------------------------------|
| `width`      | number   | null      | Custom width of container                           |
| `height`       | number   | null      | Custom height of container                        |
| `strict`     | boolean  | true      | Enables/Disbaled Automagic feature                  |

### .refresh()

The `embedo.refresh()` method can be called explicitly when you have a `change` or `resize` event, which re-calculates the dimensions of generated content.

```js
embedo.refresh()
```

### Watch Element

Embedo also adds a `watch` event to all requested DOM Elements so you can listen to them in case you need to adjust some changes to your use-case.

```js
// With Vanilla JS
document.getElementById('element-identifier').addEventListener('watch',
  function (event) {
    console.log(event, event.detail);
  });

// With jQuery
$('#element-identifier').on('watch', function (e) {
  console.log(e, e.detail);
});
```

## Example

```js
embedo.load(
  document.getElementById('element-identifier'),
  'https://twitter.com/Sh0bhit/status/797584590214926340'
);

// jQuery
embedo.load($('.my-unique-selector')[0], 'https://www.youtube.com/watch?v=Q6gYFO4iGlk');
```

## Development and Contribution

If you'd like to fix some issues or add new features, feel free to create an issue for that.
To setup environment, tests and build, use following commands:

```bash
$ npm start
$ npm run build
```

## Supports

- Facebook SDK and oEmbed
- Twitter SDK and oEmbed
- Instagram SDK and oEmbed
- YouTube Embed

