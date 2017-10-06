---
layout: post
title:  "Aurelia Breeze Client Startup"
date:   2017-10-06
desc: "aurelia, breeze"
keywords: "aurelia, breeze"
categories: [others]
tags: [Aurelia]
icon: icon-aurelia
---



Getting Started
===============

Pre Requisites
--------------

Aurelia Setup project

Dependencies
------------

-   [aurelia-binding](https://github.com/aurelia/binding)

-   [aurelia-dependency-injection](https://github.com/aurelia/dependency-injection)

-   [aurelia-fetch-client](https://github.com/aurelia/fetch-client)

-   [breeze](http://www.getbreezenow.com/breezejs)

Installs
--------

npm install aurelia-fetch-client --save

npm install aurelia-breeze --save

Update aurelia.json for path of above installs
----------------------------------------------

{

"name": "breeze-client",

"path": "../node\_modules/breeze-client",

"main": "breeze.base.debug.js",

"exports": "breeze",

"resources": \[

"breeze.modelLibrary.backingStore.js",

"breeze.dataService.webApi.js",

"breeze.dataService.odata.js",

"breeze.ajax.jQuery.js",

"breeze.uriBuilder.json.js",

"breeze.uriBuilder.odata.js"

\]

},

{

"name": "aurelia-breeze",

"path": "../node\_modules/aurelia-breeze/dist/amd",

"main": "index"

},

{

"name": "aurelia-fetch-client",

"path": "../node\_modules/aurelia-fetch-client/dist/amd",

"main": "aurelia-fetch-client"

}

Register aurelia-breeze plugin with Aurelia
-------------------------------------------

import 'breeze-client/breeze.modelLibrary.backingStore';

import 'breeze-client/breeze.dataService.webApi';

import 'breeze-client/breeze.uriBuilder.json';

export function configure(aurelia) {

aurelia.use

.standardConfiguration()

.plugin('aurelia-breeze'); // &lt;--------&lt;&lt;

aurelia.start().then(a =&gt; a.setRoot());

}

Bingo!!! You are ready to use breeze in your Aurelia application.

Error
=====

If you will use breeze.debug.js. It contains all adapters and will give
you below error due to occurrence of multiple annonymous define.

To reomove error use breeze.base.debug.js

![](media/image1.png){width="6.5in" height="2.3892246281714784in"}

Now breeze.base.debug.js needs backingStore adapter and you will see
below error.

Provide breeze-client/modelLibrary.backingStore.js via import in main.ts

![](media/image2.png){width="6.5in" height="0.896738845144357in"}

Voila, Errors are gone.

References
==========

-   <http://breeze.github.io/doc-js/>

-   <https://github.com/jdanyow/aurelia-breeze>

-   <https://github.com/Breeze/breeze.bridge.angular/issues/6>

