# Context.js

[简体中文](README.md)|English

![image](https://user-images.githubusercontent.com/22728201/147812723-6dd06424-642e-4b0a-94e9-3adbfa09450a.png)

## About

This is an enhanced version of the right-click context menu library. In the past few years, [Lsky Pro](https://github.com/wisp-x/lsky-pro)
I have been using [jakiestfu/Context.js](https://github.com/jakiestfu/Context.js).  
Although the source library has stopped updating since 2014, it still works well. But when the business was upgraded, this old version no longer met my needs, so I have this version.  
Note that this library depends on Jquery.

## Features

- Can be used with or without Twitters Bootstrap.css
- Icon support for menu items with Twitter Bootstrap icons
- Event Based Links
- Anchor Links
- Headers
- Dividers
- Recursive Menus (infinite depth)
- Vertical Space Detection (turns into a "dropup")
- Horizontal Space Detection (Drops to the left instead of right)
- Add/Delete menus Dynamically
- Even works on Inline Links
- Dynamic menu items through callbacks during menu creation
- Support to get the right-clicked element in the click callback
- Support callback events before and after the context menu is opened
- Support for dynamically displaying/hiding menu items through callback events
- Support custom menu item class and custom attributes

# Use

1. Initializing contextjs

```js
context.init({
  fadeSpeed: 100,
  filter: function ($obj) {
  },
  above: 'auto',
  preventDoubleContext: true,
  compress: false
});
```
> Please refer to the source library for configuration instructions.

2. Attaching

```js
context.attach('.item', {
  data: [
    {header: 'this is header'}, // header title
    {
      text: 'Open file',
      classes: ['open-file'], // Custom class, must be array
      attributes: { // Custom label attribute, must be an object
        'data-operate': 'open-file',
      },
      // Click the callback after the menu item
      action: function (item) { // The first parameter represents .item element
        // Use this to get the currently clicked menu item
      },
      visible: function (item) { // The first parameter represents .item element
        // In this callback, the value of bool type is returned to show / hide a menu item
      },
    },
    {divider: true}, // divider line
  ],
  // After the right mouse click, the callback before the context menu is opened
  beforeOpen: function (item) { // The first parameter represents .item element
    // If you want to get the ContextMenu event object here, please use this
  },
  // After right clicking, the callback event after the context menu is opened
  afterOpen: function (item, dropdown) { // The first parameter represents the .item element, the second parameter represents the context menu element
    // If you want to get the contextmenu event object here, please use this
  }
});
```