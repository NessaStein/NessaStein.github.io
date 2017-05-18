---
layout: post
title:  "My First Blog Borned"
date:   2017-02-17 10:47:45
comments: true
description: this is a description
tags: 
- motherfucker
share: true
---

This is a testajslfjaslfjalfjal

To use it simply grab CSS from userstyles.org, remove `@-moz-document` wrapper, paste CSS in following snippet and put it in Custom Code field in service's advanced settings:

```js
function applycss(css){
    var head = document.getElementsByTagName('head')[0];
    var s = document.createElement('style');
    s.setAttribute('type', 'text/css');
    s.appendChild(document.createTextNode(css));
    head.appendChild(s);
 }
applycss(`
// css goes here
`);
```

