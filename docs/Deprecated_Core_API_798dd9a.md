<!-- loio798dd9abcae24c8194922615191ab3f5 -->

| loio |
| -----|
| 798dd9abcae24c8194922615191ab3f5 |

<div id="loio">

view on: [demo kit nightly build](https://sdk.openui5.org/nightly/#/topic/798dd9abcae24c8194922615191ab3f5) | [demo kit latest release](https://sdk.openui5.org/topic/798dd9abcae24c8194922615191ab3f5)</div>

## Deprecated Core API

This page describes important aspects of the deprecation of the `sap.ui.core.Core` API facade, as most of its methods have been deprecated. It shows a migration path away from the deprecated legacy APIs and towards their future-proof alternatives.

***

<a name="loio798dd9abcae24c8194922615191ab3f5__section_msd_jb4_rzb"/>

### Overview of Deprecated API Methods of `Core`

The following is an alphabetical list of API methods on `sap.ui.core.Core`. Meant as a compact and practical overview, it is derived from the [API Reference](https://sdk.openui5.org/api/sap.ui.core.Core), which may provide complementary information.


<table>
<tr>
<th valign="top">

Legacy API Method

</th>
<th valign="top">

Deprecation Information

</th>
</tr>
<tr>
<td valign="top">

[`applyChanges`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/applyChanges)

</td>
<td valign="top">

Applications and controls should not call this method explicitly as the framework handles necessary rendering. The `applyChanges()` method enforces a synchronous rendering and must not be used in future-proof, productive code.

</td>
</tr>
<tr>
<td valign="top">

[`applyTheme`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/applyTheme)

</td>
<td valign="top">

Use [`Theming.setTheme()`](https://sdk.openui5.org/api/module:sap/ui/core/Theming%23methods/sap/ui/core/Theming.setTheme) instead. However, this will no longer support providing a new theme root via an "@" symbol. In URL parameters, usage of the "@" symbol is still available.

See [Setting Themes](Setting_Themes_e9fc648.md) for more details.

</td>
</tr>
<tr>
<td valign="top">

[`attachControlEvent`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachControlEvent)

</td>
<td valign="top">

Applications and controls should avoid listening to **all** control events, but rather listen to specific events provided by the control classes.

</td>
</tr>
<tr>
<td valign="top">

[`attachFormatError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachFormatError)

</td>
<td valign="top">

Use [`ManagedObject#attachFormatError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/attachFormatError) instead.

See related information for `attachParseError()`.

</td>
</tr>
<tr>
<td valign="top">

[`attachInit`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachInit)

</td>
<td valign="top">

Use [`Core.ready()`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/ready) instead. While the behavior is nearly identical, the `ready()` function also allows for Promise chaining and awaiting the Core ready state.

```
sap.ui.require(["sap/ui/core/Core"], async function(Core) {
    Core.ready(() => {
        // this callback is executed directly in case the Core is
        // already in ready state, otherwise it is executed at a later point in time
    });
    // You can also use the ready() function as a Promise, e.g.
    Core.ready().then(...)
    // or await it
    await Core.ready();
});
```

As an alternative to programmatically chaining to the Core's ready state, you can also use a dedicated `on-init` module, which will be required and executed automatically once the Core is ready:

```
<script id='sap-ui-bootstrap'
    data-sap-ui-async='true'
    data-sap-ui-resourceroots='{"my": "./"}'
    data-sap-ui-on-init='module:my/initModule'
    ...>
</script>
```



</td>
</tr>
<tr>
<td valign="top">

[`attachInitEvent`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachInitEvent)

</td>
<td valign="top">

Use [`Core.ready()`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/ready) instead.

</td>
</tr>
<tr>
<td valign="top">

[`attachIntervalTimer`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachIntervalTimer)

</td>
<td valign="top">

Use [`IntervalTrigger.addListener()`](https://sdk.openui5.org/api/sap.ui.core.IntervalTrigger%23methods/sap.ui.core.IntervalTrigger.addListener) instead.

</td>
</tr>
<tr>
<td valign="top">

[`attachLocalizationChanged`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachLocalizationChanged)

</td>
<td valign="top">

Use [`Localization#attachChange()`](https://sdk.openui5.org/api/module:sap/base/i18n/Localization%23methods/attachChange) instead.

Instead of relying on `Localization.attachChange()` and manually attaching an event handler for `localizationChanged`, we recommend to use the generic control hook **`onLocalizationChanged`** on your `sap.ui.core.Element` subclasses instead.

> ### Note:  
> The generic control hook has been renamed from `onlocalizationChanged` to `onLocalizationChanged` \(mind the capital letter "L"\).
> 
> The generic control hook captures all changes on settings exposed via the `sap/base/i18n/Localization` facade, as well as the changes to settings exposed via the`sap/base/i18n/Formatting` facade.

The old `LocalizationChanged` event was fired on each relevant localization **and** format settings change.

The `change` event of the new `Localization` facade only captures the settings that are changeable via said facade. However, if you are interested in the changes of the format settings, additionally use the `change` event of the `sap/base/i18n/Formatting` facade.

> ### Note:  
> The Event object has a different API than on the Core facade. There is no more `getParameters()`, but simple properties like the Web API events \(see the sample below\).
> 
> See [`Localization$ChangeEvent`](https://sdk.openui5.org/api/module:sap/base/i18n/Localization$ChangeEvent) or [`Formatting$ChangeEvent`](https://sdk.openui5.org/api/module:sap/base/i18n/Formatting$ChangeEvent), respectively.

Instead of the former APIs `onlocalizationChanged()` or `attachLocalizationChanged()`, see the following sample:

```
/// generic control hook
MyControl.prototype.onLocalizationChanged = function() {};
 
// Localization API
sap.ui.require([
    "sap/base/i18n/Localization",
    "sap/base/i18n/Formatting"
], (Localization, Formatting) => {
    Localization.attachChange((oEvent) => {
        // Note: The event callback has no <this> context anymore,
        // thus we use an arrow function here
 
        // Note: the Event object has a different API than on the Core facade:
        // no more getParameters(), but simple properties like the Web API events.
        // Therefore, you can access the newly set "language" like so:
        const sLanguage = oEvent.language;
    });
 
    // additional setting changes can be captured via the Formatting facade
    Formatting.attachChange((oEvent) => {
        // s.a.
    });
});
```



</td>
</tr>
<tr>
<td valign="top">

[`attachParseError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachParseError)

</td>
<td valign="top">

Use [`ManagedObject#attachParseError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/attachParseError) instead.

Overall, the events `parseError`, `validationError`, `formatError` and `validationSuccess` have been deprecated. Use the corresponding APIs on subclasses of `sap/ui/base/ManagedObject`.

Component-based applications should rather prefer framework controlled validation handling \(manifest flag `"sap.ui5"/"handleValidation"`\).

Tests and samples that are not Component-based should attach validation event listeners to a suitable control in the control tree instead.

```
sap.ui.require([
    "sap/ui/core/Component"
], async (Component) => {
    const oComponent = await Component.create({
        name: "my.component"
    });
    const fnParseErrorHandler = function () {
        // Error handling
    };
    oComponent.attachParseError(fnParseErrorHandler);
    oComponent.detachParseError(fnParseErrorHandler);
});
```



</td>
</tr>
<tr>
<td valign="top">

[`attachThemeChanged`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachThemeChanged)

</td>
<td valign="top">

For applications and test code, see [`Theming.attachApplied()`](https://sdk.openui5.org/api/module:sap/ui/core/Theming%23methods/attachApplied) as an alternative. For controls, use the generic control hook **`onThemeChanged`** on your `sap.ui.core.Element` subclasses instead.

> ### Note:  
> The Event object has a different API than on the Core facade. There is no more `getParameters()`, but simple properties like the Web API events.

> ### Caution:  
> The handler of the **`applied`** event will be executed immediately once, in case all \*.css files are loaded and there are no further requests pending for the theme.
> 
> After that, it will only be executed in case of new \*.css files, which may happen for a complete theme change or loading of additional libraries. Keep in mind that the **`onThemeChanged`** hook is not executed initially in case the theme is already applied.



</td>
</tr>
<tr>
<td valign="top">

[`attachValidationError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachValidationError)

</td>
<td valign="top">

Use [`ManagedObject#attachValidationError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/attachValidationError) instead.

See related information for `attachParseError()`.

</td>
</tr>
<tr>
<td valign="top">

[`attachValidationSuccess`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/attachValidationSuccess)

</td>
<td valign="top">

Use [`ManagedObject#attachValidationSuccess()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/attachValidationSuccess) instead.

See related information for `attachParseError()`.

</td>
</tr>
<tr>
<td valign="top">

[`byFieldGroupId`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/byFieldGroupId)

</td>
<td valign="top">

Use [`Control#getControlsByFieldGroup()`](https://sdk.openui5.org/api/sap.ui.core.Control%23methods/getControlsByFieldGroup) instead.

</td>
</tr>
<tr>
<td valign="top">

[`byId`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/byId)

</td>
<td valign="top">

Use [`Element.getElementById()`](https://sdk.openui5.org/api/sap.ui.core.Element%23methods/sap.ui.core.Element.getElementById) instead.

```
sap.ui.require(["sap/ui/core/Element"], async function(Element) {
    const oMyElement = Element.getElementById("myId");
});
```



</td>
</tr>
<tr>
<td valign="top">

[`createComponent`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/createComponent)

</td>
<td valign="top">

Use [`Component.create()`](https://sdk.openui5.org/api/sap.ui.core.Component%23methods/sap.ui.core.Component.create) instead.

</td>
</tr>
<tr>
<td valign="top">

[`createRenderManager`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/createRenderManager)

</td>
<td valign="top">

A separate `RenderManager` should not be used.

</td>
</tr>
<tr>
<td valign="top">

[`createUIArea`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/createUIArea)

</td>
<td valign="top">

Use [`Control#placeAt()`](https://sdk.openui5.org/api/sap.ui.core.Control%23methods/placeAt) instead.

</td>
</tr>
<tr>
<td valign="top">

[`detachControlEvent`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/detachControlEvent)

</td>
<td valign="top">

See `attachControlEvent()` above.

</td>
</tr>
<tr>
<td valign="top">

[`detachFormatError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/detachFormatError)

</td>
<td valign="top">

Use [`ManagedObject#detachFormatError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/detachFormatError) instead.

See related information for `attachParseError()`.

</td>
</tr>
<tr>
<td valign="top">

[`detachIntervalTimer`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/detachIntervalTimer)

</td>
<td valign="top">

Use [`IntervalTrigger.removeListener()`](https://sdk.openui5.org/api/sap.ui.core.IntervalTrigger%23methods/sap.ui.core.IntervalTrigger.removeListener) instead.

</td>
</tr>
<tr>
<td valign="top">

[`detachLocalizationChanged`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/detachLocalizationChanged)

</td>
<td valign="top">

Use [`Localization#detachChange()`](https://sdk.openui5.org/api/module:sap/base/i18n/Localization%23methods/detachChange) instead.

</td>
</tr>
<tr>
<td valign="top">

[`detachParseError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/detachParseError)

</td>
<td valign="top">

Use [`ManagedObject#detachParseError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/detachParseError) instead.

See related information for `attachParseError()`.

</td>
</tr>
<tr>
<td valign="top">

[`detachThemeChanged`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/detachThemeChanged)

</td>
<td valign="top">

See [`Theming.detachApplied()`](https://sdk.openui5.org/api/module:sap/ui/core/Theming%23methods/detachApplied) instead.

</td>
</tr>
<tr>
<td valign="top">

[`detachValidationError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/detachValidationError)

</td>
<td valign="top">

Use [`ManagedObject#detachValidationError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/detachValidationError) instead.

See related information for `attachParseError()`.

</td>
</tr>
<tr>
<td valign="top">

[`detachValidationSuccess`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/detachValidationSuccess)

</td>
<td valign="top">

Use [`ManagedObject#detachValidationSuccess()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/detachValidationSuccess) instead.

See related information for `attachParseError()`.

</td>
</tr>
<tr>
<td valign="top">

[`fireFormatError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/fireFormatError)

</td>
<td valign="top">

Use [`ManagedObject#fireFormatError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/fireFormatError) instead.

</td>
</tr>
<tr>
<td valign="top">

[`fireParseError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/fireParseError)

</td>
<td valign="top">

Use [`ManagedObject#fireParseError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/fireParseError) instead.

</td>
</tr>
<tr>
<td valign="top">

[`fireValidationError`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/fireValidationError)

</td>
<td valign="top">

Use [`ManagedObject#fireValidationError()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/fireValidationError) instead.

</td>
</tr>
<tr>
<td valign="top">

[`fireValidationSuccess`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/fireValidationSuccess)

</td>
<td valign="top">

Use [`ManagedObject#fireValidationSuccess()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/fireValidationSuccess) instead.

</td>
</tr>
<tr>
<td valign="top">

[`getApplication`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getApplication)

</td>
<td valign="top">

The `Component` class is enhanced to take care about the application code.

</td>
</tr>
<tr>
<td valign="top">

[`getComponent`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getComponent)

</td>
<td valign="top">

Use [`Component.getComponentById()`](https://sdk.openui5.org/api/sap.ui.core.Component%23methods/sap.ui.core.Component.getComponentById) instead.

</td>
</tr>
<tr>
<td valign="top">

[`getConfiguration`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getConfiguration)

</td>
<td valign="top">

See [Deprecated Configuration API](Deprecated_Configuration_API_2acafbf.md) for detailed information to handle legacy `sap.u.core.Configuration` via replacements for the respective APIs.

</td>
</tr>
<tr>
<td valign="top">

[`getControl`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getControl)

</td>
<td valign="top">

Use [`Element.getElementById()`](https://sdk.openui5.org/api/sap.ui.core.Element%23methods/sap.ui.core.Element.getElementById) instead. See example at `byId()`.

</td>
</tr>
<tr>
<td valign="top">

[`getCurrentFocusedControlId`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getCurrentFocusedControlId)

</td>
<td valign="top">

Use [`Element.getActiveElement()`](https://sdk.openui5.org/api/sap.ui.core.Element%23methods/sap.ui.core.Element.getActiveElement) to get the currently focused element. You can then retrieve the ID of that element with [`Element#getId()`](https://sdk.openui5.org/api/sap.ui.core.Element%23methods/getId). Keep in mind that `Element.getActiveElement()` may return `undefined`.

</td>
</tr>
<tr>
<td valign="top">

[`getElementById`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getElementById)

</td>
<td valign="top">

Use [`Element.getElementById()`](https://sdk.openui5.org/api/sap.ui.core.Element%23methods/sap.ui.core.Element.getElementById) instead. See example at `byId()`.

</td>
</tr>
<tr>
<td valign="top">

[`getEventBus`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getEventBus)

</td>
<td valign="top">

Use [`EventBus.getInstance()`](https://sdk.openui5.org/api/sap.ui.core.EventBus%23methods/sap.ui.core.EventBus.getInstance) for global usage instead. However, the global `EventBus` should only be used if there is no other option to communicate between different instances. Whenever possible, you should prefer native control events, View or Component \(lifecycle\) events.

```
sap.ui.require([
    "sap/ui/core/EventBus"
], (EventBus) => {
    const oEventBus = EventBus.getInstance();
});
```

If needed, a new private `EventBus` instance may be created via the constructor, which decouples it from any other parties subscribed to the global `EventBus`:

```
const oMyOwnEventBus = new EventBus();
oMyEventBus.subscribe("my-channel-id", "my-event-id")
oMyEventBus.publish("my-channel-id", "my-event-id", { /* data */ })
```



</td>
</tr>
<tr>
<td valign="top">

[`getLibraryResourceBundle`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getLibraryResourceBundle)

</td>
<td valign="top">

Use [`Lib.getResourceBundleFor()`](https://sdk.openui5.org/api/sap.ui.core.Lib%23methods/sap.ui.core.Lib.getResourceBundleFor) instead.

Note that the new API may unintentionally still load the ResourceBundle for the given library synchronously, which is to be avoided. Therefore, make sure to always either load the library beforehand or maintain it as a **Component** or **Library** dependency, so that you can prevent such synchronous loading of \*.properties files.

```
// Retrieve ResourceBundle when library was already loaded beforehand.
// This is the case for controls inside their own library
sap.ui.require(["sap/ui/core/Lib"], async (Library) => {
    // ensures the library is loaded
    await Library.load({ name: "sap.m" });
    // ResourceBundle can be retrieved
    const oRB = Library.getResourceBundleFor("sap.m")
});
```



</td>
</tr>
<tr>
<td valign="top">

[`getLoadedLibraries`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getLoadedLibraries)

</td>
<td valign="top">

Applications should avoid performing operations on all loaded libraries. This concept is reserved for the framework itself and dedicated support use cases.

</td>
</tr>
<tr>
<td valign="top">

[`getMessageManager`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getMessageManager)

</td>
<td valign="top">

Use [`Messaging`](https://sdk.openui5.org/api/module:sap/ui/core/Messaging) instead.

```
// example, replacing legacy sap.ui.getCore().getMessageManager().addMessage()
sap.ui.require([
    "sap/ui/core/Messaging",
    "sap/ui/core/message/Message
], (Messaging, Message) => {
    Messaging.addMessage(new Message({
        text: "My message text"
    }));
});
```



</td>
</tr>
<tr>
<td valign="top">

[`getModel`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getModel)

</td>
<td valign="top">

Deprecated without direct replacement. See the information on `setModel()` below for a potential use via [`ManagedObject#getModel()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/getModel) instead.

</td>
</tr>
<tr>
<td valign="top">

[`getRenderManager`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getRenderManager)

</td>
<td valign="top">

A separate `RenderManager` should not be used.

</td>
</tr>
<tr>
<td valign="top">

[`getRootComponent`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getRootComponent)

</td>
<td valign="top">

Use [`sap/ui/core/ComponentSupport`](https://sdk.openui5.org/api/module:sap/ui/core/ComponentSupport) instead. See also [Declarative API for Initial Components](Declarative_API_for_Initial_Components_82a0fce.md).

</td>
</tr>
<tr>
<td valign="top">

[`getStaticAreaRef`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getStaticAreaRef)

</td>
<td valign="top">

Use [`StaticArea.getDomRef()`](https://sdk.openui5.org/api/module:sap/ui/core/StaticArea%23methods/sap/ui/core/StaticArea.getDomRef) instead. It provides more possibilities, e.g. you can also retrieve the static UIArea directly, if needed.

```
sap.ui.require([
    "sap/ui/core/StaticArea"
], (StaticArea) => {
    // Direct replacement
    const oStaticArea = StaticArea.getDomRef();
 
    // Retrieving the static UIArea directly
    oStaticUIArea = StaticArea.getUIArea();
 
    // Check whether the given DOM element is part of the static area
    const bContainedInArea = StaticArea.contains(myControl.getDomRef())
});
```



</td>
</tr>
<tr>
<td valign="top">

[`getTemplate`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getTemplate)

</td>
<td valign="top">

Use an [`XMLView`](https://sdk.openui5.org/api/sap.ui.core.mvc.XMLView) or a [Typed View](Typed_View_e6bb33d.md) instead.

</td>
</tr>
<tr>
<td valign="top">

[`getUIArea`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getUIArea)

</td>
<td valign="top">

For access to the static UIArea, use the [`StaticArea`](https://sdk.openui5.org/api/module:sap/ui/core/StaticArea) instead.

</td>
</tr>
<tr>
<td valign="top">

[`getUIDirty`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/getUIDirty)

</td>
<td valign="top">

Applications and controls should avoid querying the rendering state and should rely on the standard rendering lifecycle of the framework.

</td>
</tr>
<tr>
<td valign="top">

[`hasModel`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/hasModel)

</td>
<td valign="top">

Use [`ManagedObject#hasModel()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/hasModel) instead.

</td>
</tr>
<tr>
<td valign="top">

[`includeLibraryTheme`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/includeLibraryTheme)

</td>
<td valign="top">

Applications and controls should avoid interfering with the loading of library.css files. All library theme files are maintained and orchestrated by the framework.

Use [`Lib.load()`](https://sdk.openui5.org/api/sap.ui.core.Lib%23methods/sap.ui.core.Lib.load) instead to ensure the loading of the corresponding theme files.

</td>
</tr>
<tr>
<td valign="top">

[`initLibrary`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/initLibrary)

</td>
<td valign="top">

Use [`Lib.init()`](https://sdk.openui5.org/api/sap.ui.core.Lib%23methods/sap.ui.core.Lib.init) instead.

```
// the object is no longer passed into sap.ui.getCore().initLibrary()
sap.ui.require(["sap/ui/core/Lib"], (Library) => {
    Library.init({
        name: "my.library",
        version: "${version}",
        dependencies: ["sap.ui.core", "..."],
        types: [
            ...
        ],
        interfaces: [],
        controls: [
            ...
        ],
        elements: [
            ...
        ],
        extensions: {
            ...
        }
    });
});
```



</td>
</tr>
<tr>
<td valign="top">

[`isInitialized`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/isInitialized)

</td>
<td valign="top">

Deprecated without replacement. It should no longer be necessary as it was mainly used to avoid accessing APIs before the Core was ready, but these other Core APIs have been deprecated as well.

```
// Nevertheless, if you still have a need for isInitialized, maybe use the following
sap.ui.require(["sap/ui/core/Core"], async function(Core) {
    let isInitialized = false;
    Core.ready(() => {
        isInitialized = true;
    });
    if (isInitialized) {
        ...
    }
});
```



</td>
</tr>
<tr>
<td valign="top">

[`isLocked`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/isLocked)

</td>
<td valign="top">

Locking the event handling of the `sap.ui.core.Core` is considered an anti-pattern and should be avoided.

</td>
</tr>
<tr>
<td valign="top">

[`isMobile`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/isMobile)

</td>
<td valign="top">

Use [`Device.browser.mobile`](https://sdk.openui5.org/api/sap.ui.Device.browser) instead.

</td>
</tr>
<tr>
<td valign="top">

[`isStaticAreaRef`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/isStaticAreaRef)

</td>
<td valign="top">

Use [`StaticArea.contains()`](https://sdk.openui5.org/api/module:sap/ui/core/StaticArea%23methods/sap/ui/core/StaticArea.contains) instead.

</td>
</tr>
<tr>
<td valign="top">

[`isThemeApplied`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/isThemeApplied)

</td>
<td valign="top">

For applications and test code, see [`Theming.attachApplied()`](https://sdk.openui5.org/api/module:sap/ui/core/Theming%23methods/attachApplied) as an alternative. For controls, use the generic control hook **`onThemeChanged`** on your `sap.ui.core.Element` subclasses instead.

See `attachThemeChanged` for related information.

</td>
</tr>
<tr>
<td valign="top">

[`loadLibrary`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/loadLibrary)

</td>
<td valign="top">

Use [`Lib.load()`](https://sdk.openui5.org/api/sap.ui.core.Lib%23methods/sap.ui.core.Lib.load) instead.

```
// instead of legacy loading via sap.ui.getCore().loadLibrary("my.library")
sap.ui.require(["sap/ui/core/Lib"], (Library) => {
    Library.load({
        name: "my.library"
    });
});
```



</td>
</tr>
<tr>
<td valign="top">

[`lock`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/lock)

</td>
<td valign="top">

Locking the event handling of the `sap.ui.core.Core` is considered an anti-pattern and should be avoided.

</td>
</tr>
<tr>
<td valign="top">

[`notifyContentDensityChanged`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/notifyContentDensityChanged)

</td>
<td valign="top">

Use [`Theming.notifyContentDensityChanged()`](https://sdk.openui5.org/api/module:sap/ui/core/Theming%23methods/sap/ui/core/Theming.notifyContentDensityChanged) instead.

</td>
</tr>
<tr>
<td valign="top">

[`registerPlugin`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/registerPlugin)

</td>
<td valign="top">

Albeit plugins are not meant for public usage, the common need to access the set of all controls/elements or all components can now be achieved using the [`sap.ui.core.Element.registry`](https://sdk.openui5.org/api/sap.ui.core.Element.registry) or [`sap.ui.core.Component.registry`](https://sdk.openui5.org/api/sap.ui.core.Component.registry) APIs, respectively.

</td>
</tr>
<tr>
<td valign="top">

[`sap.ui.core.Core.extend`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/sap.ui.core.Core.extend)

</td>
<td valign="top">

`sap.ui.core.Core` is a singleton and should not be sub-classed.

</td>
</tr>
<tr>
<td valign="top">

[`sap.ui.core.Core.getMetadata`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/sap.ui.core.Core.getMetadata)

</td>
<td valign="top">

`sap.ui.core.Core` is a singleton and the metadata of the internal class should not be accessed.

</td>
</tr>
<tr>
<td valign="top">

[`setModel`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/setModel)

</td>
<td valign="top">

Deprecated without direct replacement. The future-proof Core facade no longer acts as a model provider.

Component-based applications should prefer manifest models.

Tests and samples which are not Component-based may attach models to a suitable control in the control tree instead, e.g. via [`ManagedObject#setModel()`](https://sdk.openui5.org/api/sap.ui.base.ManagedObject%23methods/setModel).

</td>
</tr>
<tr>
<td valign="top">

[`setRoot`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/setRoot)

</td>
<td valign="top">

Use [`oControl.placeAt(oDomRef, "only")`](https://sdk.openui5.org/api/sap.ui.core.Control%23methods/placeAt) instead.

</td>
</tr>
<tr>
<td valign="top">

[`setThemeRoot`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/setThemeRoot)

</td>
<td valign="top">

Theme roots should not be changed at runtime. Instead, provide the corresponding `sap-ui-theme-roots` configuration option via either the bootstrap, meta tag, or an URL parameter. See [Setting Themes](Setting_Themes_e9fc648.md) for more details.

</td>
</tr>
<tr>
<td valign="top">

[`unlock`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/unlock)

</td>
<td valign="top">

Locking the event handling of the `sap.ui.core.Core` is considered an anti-pattern and should be avoided.

</td>
</tr>
<tr>
<td valign="top">

[`unregisterPlugin`](https://sdk.openui5.org/api/sap.ui.core.Core%23methods/unregisterPlugin)

</td>
<td valign="top">

See `registerPlugin` above.

</td>
</tr>
</table>
