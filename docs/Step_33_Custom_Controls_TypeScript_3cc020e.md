<!-- loio3cc020e232a2472c9f7fde2e99230633 -->

| loio |
| -----|
| 3cc020e232a2472c9f7fde2e99230633 |

<div id="loio">

view on: [demo kit nightly build](https://sdk.openui5.org/nightly/#/topic/3cc020e232a2472c9f7fde2e99230633) | [demo kit latest release](https://sdk.openui5.org/topic/3cc020e232a2472c9f7fde2e99230633)</div>

## Step 33: Custom Controls \(TypeScript\)

In this step, we are going to extend the functionality of OpenUI5 with a custom control. We want to rate the product shown on the detail page, so we create a composition of multiple standard controls using the OpenUI5 extension mechanism and add some glue code to make them work nicely together. This way, we can reuse the control across the app and keep all related functionality in one module.

***

### Preview

  
  
**A custom product rating control is added to the detail page**

![](images/loio21dd14c37b67473b817c8865f168f668_LowRes.png "A custom product rating control is added to the detail page")

***

<a name="loio3cc020e232a2472c9f7fde2e99230633__section_ylk_pbn_tyb"/>

### Coding

You can view all files at [OpenUI5 TypeScript Walkthrough - Step 33: Custom Controls](https://github.com/sap-samples/ui5-typescript-walkthrough/steps/33/README.md).

***

<a name="loio3cc020e232a2472c9f7fde2e99230633__section_bzj_rbn_tyb"/>

### webapp/i18n/i18n.properties

For our new product-rating custom control we will need some additional text resources: Firstly, we'll need some labels for the custom control, interacting with the user. Then we want to display a confirmation message on the detail page once a user has provided their rating.

```ini
…
# Detail Page
detailPageTitle=Walkthrough - Details
ratingConfirmation=You have rated this product with {0} stars

# Product Rating
productRatingLabelInitial=Please rate this product
productRatingLabelIndicator=Your rating: {0} out of {1}
productRatingLabelFinal=Thank you for your rating!
productRatingButton=Rate
```

The resource bundle is extended with the confirmation message and the strings that we reference inside the custom control. We can now rate a product on the detail page with our brand new control.

***

<a name="loio3cc020e232a2472c9f7fde2e99230633__section_azj_rbn_tyb"/>

### webapp/css/style.css

To layout our new custom control, we specify some additional css. We create a root class `myAppDemoWTProductRating` that sets the padding to `0.75rem`. We will use this class to specify some space around our inner controls. In a second rule we reset the vertical alignment of controls with the class `sapMRI` assigned to inside controls with the class `myAppDemoWTProductRating` to the initial value. We will need this rule to align all the controls we use with our composition.

```
html[dir="ltr"] .myAppDemoWT .myCustomButton.sapMBtn {
    margin-right: 0.125rem
}
html[dir="rtl"] .myAppDemoWT .myCustomButton.sapMBtn {
    margin-left: 0.125rem
}
.myAppDemoWT .myCustomText {
    display: inline-block;
    font-weight: bold;
}
/*  ProductRating */
.myAppDemoWTProductRating {
    padding: 0.75rem;
}
.myAppDemoWTProductRating .sapMRI {
    vertical-align: initial;
}
```

We could also do this with more HTML in the renderer, but this is the simplest way and it will only be applied inside our custom control. However, please be aware that the custom control is in your app and might have to be adjusted when the inner controls change in future versions of OpenUI5.

***

<a name="loio3cc020e232a2472c9f7fde2e99230633__section_zlk_pbn_tyb"/>

### webapp/control/ProductRating.ts \(New\)

We create a new folder `control` and a file `ProductRating.ts` that will hold our new control.

We start with importing two classes, the `Control` and the `RenderManager` from the `sap/ui/core` module. These classes are part of the OpenUI5 framework and are used for creating controls and managing their rendering. We then declare the class `ProductRating` by extending the base class `sap.ui.core.Control`.

Custom controls are small reuse components that can be created within the app very easily. Due to their nature, they are sometimes also referred to as "notepad” or “on the fly” controls. A custom control is a JavaScript object that has two special sections \(`metadata` and `renderer`\) and a number of methods that implement the functionality of the control.

First, we specify the `metadata` section. It defines the data structure and thus the API of the control. With this meta information on the properties, events, and aggregations of the control OpenUI5 automatically creates setter and getter methods and other convenience functions that can be called within the app. Next, we add the `init` method to the class. This is a special function that is called by the OpenUI5 core whenever the control is instantiated. It can be used to set up the control and prepare its content for display.

Then we add the `renderer` property. This function is responsible for rendering the control's HTML representation. It is an object with the two properties `apiVersion` and `render`. The `apiVersion` property specifies the version of the OpenUI5 rendering API to use \(in our case we specify version 2\). The `render` property is a function that takes a `RenderManager` object and the instance of the `ProductRating` control as parameters.

The renderer defines the HTML structure that will be added to the DOM tree of your app whenever the control is instantiated in a view. It is usually called initially by the core of OpenUI5 and whenever a property of the control is changed. The parameter `rm` of the render function is the OpenUI5 render manager that can be used to write strings and control properties to the HTML page.

Finally, the `ProductRating` class is exported as the default export of the module, which means that it can be imported and used in other parts of the application.

```js
import Control from "sap/ui/core/Control";
import RenderManager from "sap/ui/core/RenderManager";

/**
 * @namespace ui5.walkthrough.control
 */
export default class ProductRating extends Control {

	static readonly metadata: MetadataOptions = {
	
	}
	init(): void {
	
	}
	
	renderer = {  
		apiVersion: 2,
		render: (rm: RenderManager, control: ProductRating) => {
		}
	}
};
```

For now, the metadata section plus `init` and `render` function are empty. We will take care of this in the next step.

> ### Note:  
> Controls always extend `sap.ui.core.Control` and render themselves. You could also extend `sap.ui.core.Element` or `sap.ui.base.ManagedObject` directly if you want to reuse life cycle features of OpenUI5 including data binding for objects that are not rendered. Please refer to the API reference to learn more about the inheritance hierarchy of controls.

***

<a name="loio3cc020e232a2472c9f7fde2e99230633__section_bvh_qbn_tyb"/>

### webapp/control/ProductRating.ts

We now enhance our new custom control with the custom functionality that we need. In our case we want to create an interactive product rating, so we define a value and use three internal controls that are displayed updated by our control automatically. A `RatingIndicator` control is used to collect user input on the product, a label is displaying further information, and a button submits the rating to the app to store it.

In the `metadata` section we therefore define several properties that we make use in the implementation \(for details on individual metadata properties, see [MetadataOptions](https://sdk.openui5.org/api/sap.ui.base.ManagedObject.MetadataOptions)\):

-   Properties

    -   Value

        We define a control property `value` that will hold the value that the user selected in the rating. Getter and setter function for this property will automatically be created and we can also bind it to a field of the data model in the XML view if we like.


-   Aggregations

    As described in the first paragraph, we need three internal controls to realize our rating functionality. We therefore create three “hidden aggregations” by setting the `visibility` attribute to `hidden`. This way, we can use the models that are set on the view also in the inner controls and OpenUI5 will take care of the lifecycle management and destroy the controls when they are not needed anymore. Aggregations can also be used to hold arrays of controls but we just want a single control in each of the aggregations so we need to adjust the cardinality by setting the attribute `multiple` to `false`.

    -   `_rating`: A `sap.m.RatingIndicator` control for user input

    -   `_label`: A `sap.m.Label` to display additional information

    -   `_button`: A `sap.m.Button` to submit the rating


    > ### Note:  
    > You can define `aggregations` and `associations`
    > 
    > -   An **aggregation** is a strong relation that also manages the lifecycle of the related control, for example, when the parent is destroyed, the related control is also destroyed. Also, a control can only be assigned to one single aggregation, if it is assigned to a second aggregation, it is removed from the previous aggregation automatically.
    > 
    > -   An **association** is a weak relation that does not manage the lifecycle and can be defined multiple times. To have a clear distinction, an association only stores the ID, whereas an aggregation stores the direct reference to the control. We do not specify associations in this example, as we want to have our internal controls managed by the parent.

-   Events

    -   Change

        We specify a `change` event that the control will fire when the rating is submitted. It contains the current value as an event parameter. Applications can register to this event and process the result similar to “regular” OpenUI5 controls, which are in fact built similar to custom controls.



In the `init` function that is called by OpenUI5 automatically whenever a new instance of the control is instantiated, we set up our internal controls. We instantiate the three controls and store them in the internal aggregation by calling the framework method `setAggregation` that has been inherited from `sap.ui.core.Control`. We pass on the name of the internal aggregations that we specified above and the new control instances. We specify some control properties to make our custom control look nicer and register a `liveChange` event to the rating and a press event to the button. The initial texts for the label and the button are referenced from our `i18n` model.

Let’s ignore the other internal helper functions and event handlers for now and define our renderer. With the help of the OpenUI5 render manager and the control instance that are passed on as a reference, we can now render the HTML structure of our control. We render the start of the outer `for controls. The difference<div>` tag as `<div` and call the helper method `writeControlData` to render the ID and other basic attributes of the control inside the `div` tag. Next, we add a custom CSS class so that we can define styling rules for the custom control in our CSS file later. This CSS class and others that have been added in the view are then rendered by calling `writeClasses` on the renderer instance. Then we close the surrounding `div` tag and render three internal controls by passing the content of the internal aggregation to the render managers `renderControl` function. This will call the renderer of the controls and add their HTML to the page. Finally, we close our surrounding `<div>` tag.

The `setValue` is an overridden setter. OpenUI5 will generate a setter that updates the property value when called in a controller or defined in the XML view, but we also need to update the internal rating control in the hidden aggregation to reflect the state properly. Also, we can skip the rerendering of OpenUI5 that is usually triggered when a property is changed on a control by calling the `setProperty` method to update the control property with true as the third parameter.

Now we define the event handler for the internal rating control. It is called every time the user changes the rating. The current value of the rating control can be read from the event parameter value of the `sap.m.RatingIndicator` control. With the value we call the `setProperty` method to update the control state, then we update the `label` next to the rating to show the user which value he has selected currently and also displays the maximum value. The string with the placeholder values is read from the `i18n` model that is assigned to the control automatically.

Next, we have the `press` handler for the rating button that submits our rating. We assume that rating a product is a one-time action and first disable the rating and the button so that the user is not allowed to submit another rating. We also update the label to show a "Thank you for your rating!" message, then we fire the change event of the control and pass in the current value as a parameter so that applications that are listening to this event can react on the rating interaction.

We define the `reset` method to be able to revert the state of the control on the UI to its initial state so that the user can again submit a rating.

```js
import Control from "sap/ui/core/Control";
import RenderManager from "sap/ui/core/RenderManager";
import { MetadataOptions } from "sap/ui/core/Element";
import Label from "sap/m/Label";
import Button, { Button$PressEvent } from "sap/m/Button";
import RatingIndicator, { RatingIndicator$LiveChangeEvent } from "sap/m/RatingIndicator";
import ResourceBundle from "sap/base/i18n/ResourceBundle";
import ResourceModel from "sap/ui/model/resource/ResourceModel";

/**
 * @namespace ui5.walkthrough.control
 */
export default class ProductRating extends Control {

	static readonly metadata: MetadataOptions = {
		properties: {
			value: {
				type: "float",
				defaultValue: 0
			}
		},
		aggregations: {
			_rating: {
				type: "sap.m.RatingIndicator", 
				multiple: false,
				visibility: "hidden"
			},
			_label: {
				type: "sap.m.Label", 
				multiple: false,
				visibility: "hidden"
			},
			_button: {
				type: "sap.m.Button",
				multiple: false,
				visibility: "hidden"
			} 
		},
		events: {
			change: {
				parameters: {
					"value": "int"
				}
			}
		}
	}
	
	init(): void {
		this.setAggregation("_rating", new RatingIndicator({
			value: this.getValue(),
			iconSize: "2rem",
			visualMode: "Half",
			liveChange: this._onRate.bind(this)
		}));
		this.setAggregation("_label", new Label({
			text: "{i18n>productRatingLabelInitial}"
		}).addStyleClass("sapUiSmallMargin"));
		this.setAggregation("_button", new Button({
			text: "{i18n>productRatingButton}",
			press: this._onSubmit.bind(this)
		}).addStyleClass("sapUiTinyMarginTopBottom"));
	}

	setValue( value : "float" ): ProductRating {
		this.setProperty("value", value, true);
		(<RatingIndicator> this.getAggregation("_rating")).setValue(value);
		return this;		
	}
	
	reset(): void {
		var resourceBundle = <ResourceBundle> (<ResourceModel> this?.getModel("i18n"))?.getResourceBundle();
		
		this.setValue(0);
		(<Label> this.getAggregation("_label")).setDesign("Standard");
		(<RatingIndicator> this.getAggregation("_rating")).setEnabled(true);
		(<Label> this.getAggregation("_label")).setText(resourceBundle.getText("productRatingLabelInitial"));
		(<Button> this.getAggregation("_button")).setEnabled(true);
	}
	
	_onRate(event : RatingIndicator$LiveChangeEvent): void {
		const ressourceBundle = <ResourceBundle> (<ResourceModel> this?.getModel("i18n"))?.getResourceBundle();
		const value = event.getParameter("value");
		
		this.setProperty("value", value, true);
		
		(<Label> this.getAggregation("_label")).setText(ressourceBundle.getText("productRatingLabelIndicator", [value, (<RatingIndicator> event.getSource()).getMaxValue()]));
		(<Label> this.getAggregation("_label")).setDesign("Bold");
	}
	
	_onSubmit(event : Button$PressEvent): void {
		const resourceBundle = <ResourceBundle> (<ResourceModel> this?.getModel("i18n"))?.getResourceBundle();
		
		(<RatingIndicator> this.getAggregation("_rating")).setEnabled(false);
		(<Label> this.getAggregation("_label")).setText(resourceBundle.getText("productRatingLabelFinal"));
		(<Button> this.getAggregation("_button")).setEnabled(false);
		this.fireEvent("change", {
			value: this.getValue()
		})
	}
	
	renderer = {  
		apiVersion: 2,
		render: (rm: RenderManager, control: ProductRating) => {*HIGHLIGHT START*
			rm.openStart("div", control);
			rm.class("myAppDemoWTProductRating");
			rm.openEnd();
			rm.renderControl(<Control> control.getAggregation("_rating"));
			rm.renderControl(<Control> control.getAggregation("_label"));
			rm.renderControl(<Control> control.getAggregation("_button"));
			rm.close("div");*HIGHLIGHT END*
		}
	}
};
```

***

<a name="loio3cc020e232a2472c9f7fde2e99230633__section_s2z_hkw_4zb"/>

### Generate Control Interfaces to Resolve the TypeScript Errors

While the application would run successfully, the editor still displays an error in the `ProductRating.ts` renderer.

The solution is to use the [ts-interface-generator](https://www.npmjs.com/package/@ui5/ts-interface-generator), a small tool that scans the project for any controls \(as well as other subclasses of `sap.ui.ManagedObject`\) and generates TypeScript interface definitions declaring those generated methods:

-   Open a new terminal window in your app root folder and execute `npm install @ui5/ts-inteface-generator --save-dev` to install this package as a new development dependency in your `package.json`.

-   Run `ui5-serve`. This starts the interface generator tool in "watch" mode and creates the required interface definition \(after a short startup delay during which all existing types in the project and in UI5 are scanned\).


You can inspect the generated file`webapp/control/ProductRating.gen.d.ts` next to the control implementation. It defines an interface with the same name as the control class and declares the same module name. This causes [TypeScript to merge the definitions](https://www.typescriptlang.org/docs/handbook/declaration-merging.html) and to assume that the interface methods also exist in the class.

As a result, the TypeScript error message related to the new `ProductRating` control is gone and code completion is also available for all control API methods.

You can now stop the interface generator again, as no further control API changes will be done in this tutorial. For continuous control development with frequent API changes, you would likely add a "watch" script to `package.json` for starting this generator.

***

<a name="loio3cc020e232a2472c9f7fde2e99230633__section_a4x_1kw_4zb"/>

### webapp/controller/Detail.controller.ts

In the `Detail` controller we implement a new `onRatingChange` event that reads the value of our coustom change event that is fired when a rating has been submitted. This requires to import our new control, as well as the `ProductRating$ChangeEvent`\` type we just defined to the detail controller. To keep the sample simple we only display a message message instead of sending the rating to the back end. We therefore load the `MessageToast` module from the `sap.m` namespace to our script. In addition we need the `ResourceBundle` module from the `sap/base/i18n` namespace as well as the `ResourceModel` module from the `sap/ui/model/resource` namespace, as we want to display the confirmation message we specified in our resource bundle in the message toast.

In the `onRatingChange` event handler we extract the value of our custom change event that is fired when the rating has been submitted. We then display the confirmation message we defined in our resource bundle with the rating value in a `MessageToast` control.

In the `onObjectMatched` method, we call the `reset` method to make it possible to submit another rating as soon as the detail view is displayed for a different item.

```js
import Controller from "sap/ui/core/mvc/Controller";
import Component from "../Component";
import { Route$PatternMatchedEvent } from "sap/ui/core/routing/Route";
import History from "sap/ui/core/routing/History";
import MessageToast from "sap/m/MessageToast";
import ProductRating, { ProductRating$ChangeEvent } from "../control/ProductRating";
import ResourceBundle from "sap/base/i18n/ResourceBundle";
import ResourceModel from "sap/ui/model/resource/ResourceModel";

/**
 * @namespace ui5.walkthrough.controller
 */
export default class Detail extends Controller {

    onInit(): void {
        const router = (<Component> this.getOwnerComponent()).getRouter();
        router.getRoute("detail").attachPatternMatched(this.onObjectMatched, this);
    }
	
    onObjectMatched(event: Route$PatternMatchedEvent): void {
    
        (<ProductRating> this.byId("rating")).reset();
        this.getView().bindElement({
            path: "/" + window.decodeURIComponent((<any> event.getParameter("arguments")).invoicePath),
            model: "invoice"
        });
    }
	
    onNavBack(): void {
        const history = History.getInstance();
        const previousHash = history.getPreviousHash();
		
        if (previousHash !== undefined) {
            window.history.go(-1);
        } else {
            const router = (<Component> this.getOwnerComponent()).getRouter();
            router.navTo("overview", {}, true);
        }
    }    
   
    onRatingChange(event: ProductRating$ChangeEvent): void {
        const value = event.getParameter("value");
        const resourceBundle = <ResourceBundle> (<ResourceModel> this?.getView().getModel("i18n"))?.getResourceBundle();
		
        MessageToast.show(resourceBundle.getText("ratingConfirmation", [value]));
    }
};
```

***

### webapp/view/Detail.view.xml

All we need now is to add our new control to the detail view. To do so we must add a new namespace `wt`on the view so that we can reference our custom controls easily in the view. We then add an instance of the `ProductRating` control to our detail page and register our event handler for the change event. As we want to reset the value when navigating away, we need to assign an ID to the control. To have a proper layout, we also add a margin style class.

```xml
<mvc:View
	controllerName="ui5.walkthrough.controller.Detail"
	xmlns="sap.m"
	xmlns:mvc="sap.ui.core.mvc"
	xmlns:wt="ui5.walkthrough.control">
	<Page
		title="{i18n>detailPageTitle}"
		showNavButton="true"
		navButtonPress=".onNavBack">
		<ObjectHeader
			intro="{invoice>ShipperName}"
			title="{invoice>ProductName}"/>
		<wt:ProductRating 
			id="rating" 
			class="sapUiSmallMarginBeginEnd" 
			change=".onRatingChange"/>
	</Page>
</mvc:View>

```

We can now rate a product on the detail page with our brand new control.

***

<a name="loio3cc020e232a2472c9f7fde2e99230633__section_zpb_2kw_4zb"/>

### webapp/control/ProductRating.ts

When opening the detail page you'll see the following note in the console informing you that there is still something missing in our `ProductRating` script:

```
NOTE:
Class ProductRating in file [..]/webapp/control/ProductRating.ts needs to contain the following constructors,
in order to make TypeScript aware of the possible constructor settings. 
Please copy&paste the block manually, as the ts-interface-generator will not touch your source files:
===== BEGIN =====
// The following three lines were generated and should remain as-is  
// to make TypeScript aware of the constructor signatures
constructor(idOrSettings?: string | $ProductRatingSettings);
constructor(id?: string, settings?: $ProductRatingSettings);
constructor(id?: string, settings?: $ProductRatingSettings) { super(id, settings); }
===== END =====
```

To complete the setup of the generated interface, we follow the instructions and add the block between the BEGIN and END line into the `ProductRating` class body in the file `webapp/control/ProductRating.ts`.

```js
import Control from "sap/ui/core/Control";
import RenderManager from "sap/ui/core/RenderManager";
import { MetadataOptions } from "sap/ui/core/Element";
import Label from "sap/m/Label";
import Button, { Button$PressEvent } from "sap/m/Button";
import RatingIndicator, { RatingIndicator$LiveChangeEvent } from "sap/m/RatingIndicator";
import ResourceBundle from "sap/base/i18n/ResourceBundle";
import ResourceModel from "sap/ui/model/resource/ResourceModel";

/**
 * @namespace ui5.walkthrough.control
 */
export default class ProductRating extends Control {

	// The following three lines were generated and should remain as-is 
	// to make TypeScript aware of the constructor signatures
	constructor(idOrSettings?: string | $ProductRatingSettings);
	constructor(id?: string, settings?: $ProductRatingSettings);
	constructor(id?: string, settings?: $ProductRatingSettings) { super(id, settings); }	
    ...
```

Adding the block at this position provides the constructors and the structure of the constructor settings object. As result, the constructor signatures with and without control ID are available. Furthermore, TypeScript checks the settings you give in the constructor and suggests the available ones, like the direction property.

***

### Conventions

-   Put custom controls in the `control` folder of your app.


**Parent topic:**[Walkthrough Tutorial \(TypeScript\)](Walkthrough_Tutorial_TypeScript_dad1905.md "In this tutorial we'll introduce you to all major development paradigms of OpenUI5. We'll demonstrate the use of TypeScript with OpenUI5 and highlight the specific characteristics of this approach.")

**Next:**[Step 32: Routing Back and History \(TypeScript\)](Step_32_Routing_Back_and_History_TypeScript_ae61211.md "Now we can navigate to our detail page and display an invoice, but we cannot go back to the overview page yet. We'll add a back button to the detail page and implement a function that shows our overview page again.")

**Previous:**[Step 34: Responsiveness \(TypeScript\)](Step_34_Responsiveness_TypeScript_e5577bb.md "In this step, we improve the responsiveness of our app. OpenUI5 applications can be run on phone, tablet, and desktop devices and we can configure the application to make best use of the screen estate for each scenario. Fortunately, OpenUI5 controls like the sap.m.Table already deliver a lot of features that we can use.")

**Related Information**  


[Developing Controls](Developing_Controls_8dcab00.md "You can create own content for OpenUI5. To develop controls in JavaScript, you can either extend existing controls or create new ones.")

[Defining the Control Metadata](Defining_the_Control_Metadata_7b52540.md "Control metadata consists of properties, events, as well as aggregations and associations.")

[API Reference: `sap.m.RatingIndicator`](https://sdk.openui5.org/api/sap.m.RatingIndicator)

[Samples: `sap.m.RatingIndicator` ](https://sdk.openui5.org/entity/sap.m.RatingIndicator)

[API Reference: `sap.m.Label`](https://sdk.openui5.org/api/sap.m.Label)

[Samples: `sap.m.Label` ](https://sdk.openui5.org/entity/sap.m.Label)

[API Reference: `sap.m.Button`](https://sdk.openui5.org/api/sap.m.Button)

[Samples: `sap.m.Button` ](https://sdk.openui5.org/entity/sap.m.Button)

[API Reference: `sap.ui.core.Control`](https://sdk.openui5.org/api/sap.ui.core.Control)

[API Reference: `sap.ui.core.Element`](https://sdk.openui5.org/api/sap.ui.core.Element)

[API Reference: `sap.ui.base.ManagedObject`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject)

[NPM Package: `ui5/ts-interface-generator`](https://www.npmjs.com/package/@ui5/ts-interface-generator)

[TypeScript: Declaration Merging](https://www.typescriptlang.org/docs/handbook/declaration-merging.html)
