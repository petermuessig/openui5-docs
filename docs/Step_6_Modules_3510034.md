<!-- loio3510034eb6274fd8a8fb7d65c2f1aa46 -->

| loio |
| -----|
| 3510034eb6274fd8a8fb7d65c2f1aa46 |

<div id="loio">

view on: [demo kit nightly build](https://sdk.openui5.org/nightly/#/topic/3510034eb6274fd8a8fb7d65c2f1aa46) | [demo kit latest release](https://sdk.openui5.org/topic/3510034eb6274fd8a8fb7d65c2f1aa46)</div>

## Step 6: Modules

In OpenUI5, resources are often referred to as modules. In this step, we replace the alert from the last exercise with a proper Message Toast from the `sap.m` library.

***

### Preview

  
  
**A message toast displays the "Hello World" message**

![](images/loio2f629a95211f49afa367b60d233fb390_LowRes.png "A message toast displays the "Hello World" message")

***

<a name="loio3510034eb6274fd8a8fb7d65c2f1aa46__section_nlr_cvc_syb"/>

### Coding

You can view and download all files at [Walkthrough - Step 6](https://sdk.openui5.org/entity/sap.m.tutorial.walkthrough/sample/sap.m.tutorial.walkthrough.06).

***

<a name="loio3510034eb6274fd8a8fb7d65c2f1aa46__section_olr_cvc_syb"/>

### webapp/controller/App.controller.js

```js
sap.ui.define([
   "sap/ui/core/mvc/Controller",
   "sap/m/MessageToast"
], (Controller, MessageToast) => {
   "use strict";

   return Controller.extend("ui5.walkthrough.controller.App", {
      onShowHello() {
         MessageToast.show("Hello World");
      }
   });
});
```

We extend the array of required modules with the fully qualified path to `sap/m/MessageToast`. Once both modules, `Controller` and `MessageToast`, are loaded, the callback function is called, and we can make use of both objects by accessing the parameters passed to the function.

This Asynchronous Module Definition \(AMD\) syntax allows to clearly separate the module loading from the code execution and greatly improves the performance of the application. The browser can decide when and how the resources are loaded prior to code execution.

***

### Conventions

-   Use `sap.ui.define` for controllers and all other JavaScript modules to define a global namespace. With the namespace, the object can be addressed throughout the application.

-   Use `sap.ui.require` for asynchronously loading dependencies but without declaring a namespace, for example code that just needs to be executed, but does not need to be called from other code.

-   Use the name of the artifact to load for naming the function parameters \(without namespace\).


**Related Information**  


[API Reference: `sap.ui.define`](https://sdk.openui5.org/api/sap.ui/methods/sap.ui.define)

[API Reference: `sap.ui.require`](https://sdk.openui5.org/api/sap.ui/methods/sap.ui.require)
