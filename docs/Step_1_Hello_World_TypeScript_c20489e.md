<!-- loioc20489e2a59d46e99c83f0510392cb6c -->

| loio |
| -----|
| c20489e2a59d46e99c83f0510392cb6c |

<div id="loio">

view on: [demo kit nightly build](https://sdk.openui5.org/nightly/#/topic/c20489e2a59d46e99c83f0510392cb6c) | [demo kit latest release](https://sdk.openui5.org/topic/c20489e2a59d46e99c83f0510392cb6c)</div>

## Step 1: Hello World! \(TypeScript\)

As you know OpenUI5 is all about HTML5. Let’s get started with building a first “Hello World” with only HTML.

***

### Preview

  
  
**The browser shows the text "Hello World"**

![The graphic has an explanatory text.](images/loio1dd456361379431aab7e5bcdaaeff00f_LowRes.png "The browser shows the text "Hello World"")

***

<a name="loioc20489e2a59d46e99c83f0510392cb6c__section_js2_mhx_kzb"/>

### Coding

You can view and download all files at [UI5 TypeScript Walkthrough - Step 1](https://github.com/sap-samples/ui5-typescript-walkthrough/steps/01/README.md).

Create a folder on your local machine which will contain all the sources of the app we're going to build. We'll refer to this folder as the “app root directory”.

***

<a name="loioc20489e2a59d46e99c83f0510392cb6c__section_ks2_mhx_kzb"/>

### webapp/index.html \(New\)

Create a new folder named `webapp` in the app root directory. It will contain all the sources that become available in the browser later. We'll refer to this folder as the "webapp folder".

Create a new HTML file named `index.html` in your webapp folder and enter the following content:

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title>UI5 TypeScript Walkthrough</title>
</head>
<body>
	<div>Hello World</div>
</body>
</html>
```

> ### Note:  
> An HTML document consists basically of two sections: head and body. The head part will be used by the browser to process the document.
> 
> Using meta tags, we can influence the behavior of the browser. In this case, we tell the browser to use `UTF-8` as the document character set.
> 
> We also give our app a title that will be displayed in the browser. Our hard-coded title can be overruled by the app, for example to show a title in the language of the user. The body part describes the layout of the page. In our case, we simply display “Hello World” by using a `div` tag.

***

<a name="loioc20489e2a59d46e99c83f0510392cb6c__section_czs_c3x_kzb"/>

### webapp/manifest.json \(New\)

The manifest file is called the **descriptor for applications, components, and libraries** and is also referred to as the “descriptor” or “app descriptor”. It's stored in the `webapp` folder and read by OpenUI5 to instantiate a component. Even though we don't have a component yet \(this is part of [Step 9: Component Configuration \(TypeScript\)](Step_9_Component_Configuration_TypeScript_f9d0e2f.md)\), we need this file already now as we'd like to use UI5 Tooling for development, which requires an app descriptor.

That's why we now create a new file named `manifest.json` in the webapp folder and specify its essential attributes:

-   The `_version` attribute describes the **descriptor format version** and is mandatory. Features might be added or changed in future versions of the descriptor, and the version number helps tools that read the descriptor to identify the application settings. Every new version of OpenUI5 comes with a new version of the app descriptor. As we plan to define OpenUI5 version 1.120 as the minimum required version to be used with our app, we need to specify 1.60.0 as the descriptor format version.

    > ### Note:  
    > You can look up the matching `_version` number for each OpenUI5 release in [this table](https://github.com/SAP/ui5-manifest/blob/-/mapping.json).

-   The **`sap.app`** namespace contains application-specific attributes, the following of which are mandatory:

    -   `id`: The namespace of our application component. The ID must be provided in dot notation and must not exceed 70 characters. It specifies an ID for the project that must be unique in the system and must match the project namespace.

    -   `title`: Title of the application

        > ### Note:  
        > We recommend to make the title language-dependent. We'll describe how this is done in [Step 10: Descriptor for Applications \(TypeScript\)](Step_10_Descriptor_for_Applications_TypeScript_2a46b75.md). For now, we are satisfied with a static title.

    -   `applicationVersion`: Specifies the version of the app using semantic versioning

    -   `type`: Not a mandatory attribute, but as a project description it makes sense to configure this as well. We describe an `application` here.



```
{
  "_version": "1.60.0",
  "sap.app": {
    "id": "ui5.walkthrough"
    "type": "application",
    "title": "UI5 Walkthrough",
    "applicationVersion": {
      "version": "1.0.0"
    }
  }
}
```

> ### Note:  
> In this tutorial step, we only enter the most basic settings and parameters of the app descriptor file. In some development environments, you may get validation errors because some settings are missing; you can ignore them in this context. [Step 10: Descriptor for Applications](Step_10_Descriptor_for_Applications_8f93bf2.md) explains the purpose of the file in general and describes some additional configuration options.

***

<a name="loioc20489e2a59d46e99c83f0510392cb6c__section_e2v_fmx_kzb"/>

### UI5 Tooling

The following steps are tailored for using this project with [UI5 Tooling](Development_Environment_7bb04e0.md).

***

<a name="loioc20489e2a59d46e99c83f0510392cb6c__section_mfb_4mx_kzb"/>

### package.json \(New\)

We create a new file called `package.json` in the app root directory. It allows us to execute commands and consume packages from the [npm registry](https://www.npmjs.com/) via the npm command line interface.

Enter the following content:

```
{
  "name": "ui5.walkthrough",
  "version": "1.0.0",
  "description": "The UI5 walkthrough application",
  "scripts": {
      "start": "ui5 serve -o index.html"
  }
}

```

Next, we install the UI5 CLI and add it as development dependency to our project. For this, we open a terminal in the app root folder and execute the following command:

`npm install --save-dev @ui5/cli`.

Finally, we initialize the UI5 Tooling configuration for our project by executing the command `ui5 init` in the app root folder. This will generate a `ui5.yaml` file in our app root directory, which is essential for using UI5 Tooling with our project.

Execute `npm start` to start the web server and to open a new browser window hosting your newly created `index.html`.

**Parent topic:**[Walkthrough Tutorial \(TypeScript\)](Walkthrough_Tutorial_TypeScript_dad1905.md "In this tutorial we'll introduce you to all major development paradigms of OpenUI5. We'll demonstrate the use of TypeScript with OpenUI5 and highlight the specific characteristics of this approach.")

**Previous:**[Step 2: Bootstrap \(TypeScript\)](Step_2_Bootstrap_TypeScript_32b14d8.md "Before we can do something with OpenUI5, we need to load and initialize it. This process of loading and initializing OpenUI5 is called bootstrapping. Once this bootstrapping is finished, we simply display an alert.")

**Related Information**  


[Descriptor for Applications, Components, and Libraries \(manifest.json\)](Descriptor_for_Applications_Components_and_Libraries_manifest_json_be0cf40.md "The descriptor for applications, components, and libraries (in short: app descriptor) is inspired by the WebApplication Manifest concept introduced by the W3C. The descriptor provides a central, machine-readable, and easy-to-access location for storing metadata associated with an application, an application component, or a library.")

[Development Environment](Development_Environment_7bb04e0.md "This part of the documentation introduces you to some common and recommended use cases for the installation, configuration, and setup of OpenUI5 development environments.")

[App Development](App_Development_b1fbe1a.md "There are several ways to develop OpenUI5 applications. Select the one that meets the requirements of your projects and your expectations best.")

[UI5 Tooling: Getting Started](https://sap.github.io/ui5-tooling/stable/pages/GettingStarted/)
