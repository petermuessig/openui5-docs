<!-- loioaad03b5942bf4be481698ecf43ec295c -->

| loio |
| -----|
| aad03b5942bf4be481698ecf43ec295c |

<div id="loio">

view on: [demo kit nightly build](https://sdk.openui5.org/nightly/#/topic/aad03b5942bf4be481698ecf43ec295c) | [demo kit latest release](https://sdk.openui5.org/topic/aad03b5942bf4be481698ecf43ec295c)</div>

## What's New in OpenUI5 1.76

With this release OpenUI5 is upgraded from version 1.75 to 1.76.

***

** **


<table>
<tr>
<th valign="top">

Version



</th>
<th valign="top">

Type



</th>
<th valign="top">

Category



</th>
<th valign="top">

Title



</th>
<th valign="top">

Description



</th>
<th valign="top">

Action



</th>
<th valign="top">

Available as of



</th>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 New 



</td>
<td valign="top">

 Feature 



</td>
<td valign="top">

 **Team Calendar** 



</td>
<td valign="top">

**Team Calendar**

We have added a new demo application - the Team Calendar. It demonstrates the integration between `sap.m.PlanningCalendar` and `sap.m.SinglePlanningCalendar` controls, sharing the same data source. The Team Calendar can be used as a starting point for building a fully functional complex application. Find it in the [Demo Apps](https://sdk.openui5.orgdemoapps).

<sub>New•Feature•Info Only•1.76</sub>



</td>
<td valign="top">

Info Only



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Feature 



</td>
<td valign="top">

 **Card Explorer** 



</td>
<td valign="top">

**Card Explorer**

-   The Component card sample in the Explore section has been enhanced. To facilitate developers, we have added the option to download the bundle of all the files in the sample.
-   All the properties in the Learn section are now listed with their Since attribute. This will inform developers since which version each feature is available.

For more information, see [Card Explorer](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/index.html).

<sub>Changed•Feature•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Feature 



</td>
<td valign="top">

 **One Page Acceptance Tests \(OPA5\)** 



</td>
<td valign="top">

**One Page Acceptance Tests \(OPA5\)**

We've introduced `Drag` and `Drop` actions to OPA5 to help with the most common cases. For more information, see [Simulating User Interactions on Controls](Simulating_User_Interactions_on_Controls_8615a0b.md), the [API Reference](https://sdk.openui5.org/api/sap.ui.test.actions) and the [Sample](https://sdk.openui5.org/entity/sap.ui.test.Opa5/sample/sap.ui.core.sample.OpaAction).

<sub>Changed•Feature•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Feature 



</td>
<td valign="top">

 **OpenUI5 OData V2 Model** 



</td>
<td valign="top">

**OpenUI5 OData V2 Model**

The new version of the OpenUI5 OData V2 model introduces the following features:

-   A new `transitionMessagesOnly` binding parameter is provided for the `sap.ui.model.odata.v2.ODataListBinding` class.
-   The `updateAggregatedMessages` parameter of `sap.ui.model.odata.v2.ODataModel#read` is now public.
-   Existing server messages can be retrieved from the model using the `sap.ui.model.Context#getMessages` method.

<sub>Changed•Feature•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Feature 



</td>
<td valign="top">

 **OpenUI5 OData V4 Model** 



</td>
<td valign="top">

**OpenUI5 OData V4 Model**

The new version of the OpenUI5 OData V4 model introduces the following features:

-   You can now access the binding parameter of an operation, as described in [OData Operations](OData_Operations_b54f789.md).
-   A property path provided to `sap.ui.model.odata.v4.Context#requestSideEffects` can be given the suffix "`*`" to enforce re-reading of all properties of the related entity.

    For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.model.odata.v4.Context%23methods/requestSideEffects).


> ### Restriction:  
> Due to the limited feature scope of this version of the OpenUI5 OData V4 model, check that all required features are in place before developing applications. Double-check the detailed documentation of the features, as certain parts of a feature may be missing. While we aim to be compatible with existing controls, some controls might not work due to small incompatibilities compared to `sap.ui.model.odata.(v2.)ODataModel`, or due to missing features in the model \(such as tree binding\). This also applies to controls such as `TreeTable` and `AnalyticalTable`, which are not supported in combination with the OpenUI5 OData V4 model. The interface for applications has been changed for easier and more efficient use of the model. For a summary of these changes, see [Changes Compared to OData V2 Model](Changes_Compared_to_OData_V2_Model_abd4d7c.md).

For more information, see [OData V4 Model](OData_V4_Model_5de13cf.md), the [API Reference](https://sdk.openui5.org/api/sap.ui.model.odata.v4), and the [Samples](https://sdk.openui5.org/entity/sap.ui.model.odata.v4.ODataModel) in the Demo Kit.

<sub>Changed•Feature•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.f.FlexibleColumnLayout`** 



</td>
<td valign="top">

**`sap.f.FlexibleColumnLayout`**

-   With the new `autoFocus` property, we’ve introduced the possibility to enable/disable the autofocus functionality of the `FlexibleColumnLayout` control.For more information, see the [API Reference](https://sdk.openui5.org/api/sap.f.FlexibleColumnLayout) and the [Sample](https://sdk.openui5.org/entity/sap.f.FlexibleColumnLayout/sample/sap.f.sample.FlexibleColumnLayoutWithOneColumnStart).

-   We’ve introduced the `columnResize` event, which is fired when the resizing of each column of the control is complete.For more information, see the [API Reference](https://sdk.openui5.org/api/sap.f.FlexibleColumnLayout%23events/columnResize).


<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.m.FacetFilter`** 



</td>
<td valign="top">

**`sap.m.FacetFilter`**

Optimization regarding the initial database service query has been introduced. There are cases when the `items` aggregation for the `FacetFilterList` could take a long time fetching data from the database service. Now we have added а `search` event, that fires when the `FacetFilterList` is opened. This enables developers to register a handler function to prevent the default filtering behavior by calling the `sap.ui.base.Event.prototype.preventDefault` function. As a result, no list items are loaded initially. In this case, the developers have to define the filtering behavior at the application level inside the `search` event handler function. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.m.FacetFilter) and the [Samples](https://sdk.openui5.org/entity/sap.m.FacetFilter).

<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.m.List`, `sap.m.Table`, `sap.m.Tree`** 



</td>
<td valign="top">

**`sap.m.List`, `sap.m.Table`, `sap.m.Tree`**

New indication colors are now available \(provided by the `sap.ui.core.IndicationColor` enumeration\) that can be used for highlighting table rows. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.core.IndicationColor).

<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.m.plugins.DataStateIndicator`** 



</td>
<td valign="top">

**`sap.m.plugins.DataStateIndicator`**

We made some improvements to this plugin class and the messages shown for the data state:

-   A new refresh function of the messages for each data state is available that re-evaluates the filter and then refreshes the message strip based on that information.

-   The `filter` property that is defined by the application can now also take the related control into account, along with the message, using the respective parameters.


For more information, see the [API Reference](https://sdk.openui5.org/api/sap.m.plugins.DataStateIndicator).

<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.m.Table`** 



</td>
<td valign="top">

**`sap.m.Table`**

An automatic pop-in mode has been enabled for the responsive table. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.m.Table%23methods/getAutoPopinMode) for the related method, the [API Reference](https://sdk.openui5.org/api/sap.m.Column%23controlProperties) for the related properties, and the [Sample](https://sdk.openui5.org/entity/sap.m.Table/sample/sap.m.sample.TableAutoPopin).

<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.ui.integration.widgets.Card`** 



</td>
<td valign="top">

**`sap.ui.integration.widgets.Card`**

-   We have added a `type` property for the configuration parameters inside a card. This property defines the data type of the parameter. Currently the `type` property is used only in UI adaptation at design time. For more information, see the [Manifest Parameters](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/learn/features/manifestParameters) section in the Card Explorer.
-   We have added support for the destinations to be resolved by the host environment. In the manifest, the card developer indicates the name of the destination and the request, which depends on this destination. On the host environment side, the host application developer creates a method that resolves the given destination name to a URL. For more information, see [Destinations](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/learn/features/destinations) in the Card Explorer.
-   We have introduced optional application-level Host Actions that interact with the host environment. These specific actions are displayed by the card and processed back in the host environment. For example, sharing or removing a card. For more information, see [Host Actions](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/learn/features/hostActions) in the Card Explorer.
-   A new `JsonDateTime` parser is now used to properly parse dates. Some `DateTime` values may appear in JSON files as `DateTime Wire` format strings like `/Date(700000+0500)/`. The parser automatically splits the date string into parts, taking into account the time zone offset if present, and returns a valid date object. For more information, see [DateTime Wire Format](https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/stand-alone-json-serialization?redirectedfrom=MSDN#datetime-wire-format).

<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.ui.table.AnalyticalTable`, `sap.ui.table.Table`, `sap.ui.table.TreeTable`** 



</td>
<td valign="top">

**`sap.ui.table.AnalyticalTable`, `sap.ui.table.Table`, `sap.ui.table.TreeTable`**

-   New indication colors are now available \(provided by the `sap.ui.core.IndicationColor` enumeration\) that can be used for highlighting table rows. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.core.IndicationColor).

-   The resizing of columns has been changed to improve the usability on tablet devices.


<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.ui.table.AnalyticalTable`, `sap.ui.table.Table, sap.ui.table.TreeTable`** 



</td>
<td valign="top">

**`sap.ui.table.AnalyticalTable`, `sap.ui.table.Table, sap.ui.table.TreeTable`**

`sap.ui.table.plugins.MultiSelectionPlugin` for these tables has been enhanced and now provides the following functions:

-   The selection of indices outside of data boundaries is now no longer possible, because the binding length is taken into account.

-   A validation takes place to prevent errors from occurring due to the selection of unsuitable parameters.

-   Methods that change the selection now return a `Promise` that is resolved after a selection has been made.

-   A `customPayload` parameter has been added to the `selectionChange` event to allow event listeners to make use of custom event data.


For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.table.plugins.MultiSelectionPlugin) and the [Sample](https://sdk.openui5.org/entity/sap.ui.table.Table/sample/sap.ui.table.sample.MultiSelectionPlugin).

<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
<tr>
<td valign="top">

 1.76 



</td>
<td valign="top">

 Changed 



</td>
<td valign="top">

 Control 



</td>
<td valign="top">

 **`sap.ui.unified.calendar.Month`** 



</td>
<td valign="top">

**`sap.ui.unified.calendar.Month`**

We have enabled custom colors to be used with the `specialDates` aggregation in `sap.m.PlanningCalendar`, `sap.m.SinglePlanningCalendar`, and `sap.ui.unified.Calendar` controls. This enhancement harmonizes with the `legend` aggregation where custom colors were already available. It is implemented with the new `color` property of type `sap.ui.core.CSSColor` in the `sap.ui.unified.DateTypeRange` control. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.unified.DateTypeRange) and the [Samples](https://sdk.openui5.org/entity/sap.m.PlanningCalendar).

<sub>Changed•Control•Info Only•1.76</sub>



</td>
<td valign="top">

 Info Only 



</td>
<td valign="top">

2020-03-26



</td>
</tr>
</table>

**Parent topic:** [Previous Versions](Previous_Versions_6660a59.md "")

**Related Information**  


[What's New in OpenUI5 1.108](What_s_New_in_OpenUI5_1_108_66e33f0.md "With this release OpenUI5 is upgraded from version 1.107 to 1.108.")

[What's New in OpenUI5 1.107](What_s_New_in_OpenUI5_1_107_d4ff916.md "With this release OpenUI5 is upgraded from version 1.106 to 1.107.")

[What's New in OpenUI5 1.106](What_s_New_in_OpenUI5_1_106_5b497b0.md "With this release OpenUI5 is upgraded from version 1.105 to 1.106.")

[What's New in OpenUI5 1.105](What_s_New_in_OpenUI5_1_105_4d6c00e.md "With this release OpenUI5 is upgraded from version 1.104 to 1.105.")

[What's New in OpenUI5 1.104](What_s_New_in_OpenUI5_1_104_69e567c.md "With this release OpenUI5 is upgraded from version 1.103 to 1.104.")

[What's New in OpenUI5 1.103](What_s_New_in_OpenUI5_1_103_0e98c76.md "With this release OpenUI5 is upgraded from version 1.102 to 1.103.")

[What's New in OpenUI5 1.102](What_s_New_in_OpenUI5_1_102_f038c99.md "With this release OpenUI5 is upgraded from version 1.101 to 1.102.")

[What's New in OpenUI5 1.101](What_s_New_in_OpenUI5_1_101_7733b00.md "With this release OpenUI5 is upgraded from version 1.100 to 1.101.")

[What's New in OpenUI5 1.100](What_s_New_in_OpenUI5_1_100_27dec1d.md "With this release OpenUI5 is upgraded from version 1.99 to 1.100.")

[What's New in OpenUI5 1.99](What_s_New_in_OpenUI5_1_99_4f35848.md "With this release OpenUI5 is upgraded from version 1.98 to 1.99.")

[What's New in OpenUI5 1.98](What_s_New_in_OpenUI5_1_98_d9f16f2.md "With this release OpenUI5 is upgraded from version 1.97 to 1.98.")

[What's New in OpenUI5 1.97](What_s_New_in_OpenUI5_1_97_fa0e282.md "With this release OpenUI5 is upgraded from version 1.96 to 1.97.")

[What's New in OpenUI5 1.96](What_s_New_in_OpenUI5_1_96_7a9269f.md "With this release OpenUI5 is upgraded from version 1.95 to 1.96.")

[What's New in OpenUI5 1.95](What_s_New_in_OpenUI5_1_95_a1aea67.md "With this release OpenUI5 is upgraded from version 1.94 to 1.95.")

[What's New in OpenUI5 1.94](What_s_New_in_OpenUI5_1_94_c40f1e6.md "With this release OpenUI5 is upgraded from version 1.93 to 1.94.")

[What's New in OpenUI5 1.93](What_s_New_in_OpenUI5_1_93_f273340.md "With this release OpenUI5 is upgraded from version 1.92 to 1.93.")

[What's New in OpenUI5 1.92](What_s_New_in_OpenUI5_1_92_1ef345d.md "With this release OpenUI5 is upgraded from version 1.91 to 1.92.")

[What's New in OpenUI5 1.91](What_s_New_in_OpenUI5_1_91_0a2bd79.md "With this release OpenUI5 is upgraded from version 1.90 to 1.91.")

[What's New in OpenUI5 1.90](What_s_New_in_OpenUI5_1_90_91c10c2.md "With this release OpenUI5 is upgraded from version 1.89 to 1.90.")

[What's New in OpenUI5 1.89](What_s_New_in_OpenUI5_1_89_e56cddc.md "With this release OpenUI5 is upgraded from version 1.88 to 1.89.")

[What's New in OpenUI5 1.88](What_s_New_in_OpenUI5_1_88_e15a206.md "With this release OpenUI5 is upgraded from version 1.87 to 1.88.")

[What's New in OpenUI5 1.87](What_s_New_in_OpenUI5_1_87_b506da7.md "With this release OpenUI5 is upgraded from version 1.86 to 1.87.")

[What's New in OpenUI5 1.86](What_s_New_in_OpenUI5_1_86_4c1c959.md "With this release OpenUI5 is upgraded from version 1.85 to 1.86.")

[What's New in OpenUI5 1.85](What_s_New_in_OpenUI5_1_85_1d18eb5.md "With this release OpenUI5 is upgraded from version 1.84 to 1.85.")

[What's New in OpenUI5 1.84](What_s_New_in_OpenUI5_1_84_dc76640.md "With this release OpenUI5 is upgraded from version 1.82 to 1.84.")

[What's New in OpenUI5 1.82](What_s_New_in_OpenUI5_1_82_3a8dd13.md "With this release OpenUI5 is upgraded from version 1.81 to 1.82.")

[What's New in OpenUI5 1.81](What_s_New_in_OpenUI5_1_81_f5e2a21.md "With this release OpenUI5 is upgraded from version 1.80 to 1.81.")

[What's New in OpenUI5 1.80](What_s_New_in_OpenUI5_1_80_8cee506.md "With this release OpenUI5 is upgraded from version 1.79 to 1.80.")

[What's New in OpenUI5 1.79](What_s_New_in_OpenUI5_1_79_99c4cdc.md "With this release OpenUI5 is upgraded from version 1.78 to 1.79.")

[What's New in OpenUI5 1.78](What_s_New_in_OpenUI5_1_78_f09b63e.md "With this release OpenUI5 is upgraded from version 1.77 to 1.78.")

[What's New in OpenUI5 1.77](What_s_New_in_OpenUI5_1_77_c46b439.md "With this release OpenUI5 is upgraded from version 1.76 to 1.77.")

[What's New in OpenUI5 1.75](What_s_New_in_OpenUI5_1_75_5cbb62d.md "With this release OpenUI5 is upgraded from version 1.74 to 1.75.")

[What's New in OpenUI5 1.74](What_s_New_in_OpenUI5_1_74_c22208a.md "With this release OpenUI5 is upgraded from version 1.73 to 1.74.")

[What's New in OpenUI5 1.73](What_s_New_in_OpenUI5_1_73_231dd13.md "With this release OpenUI5 is upgraded from version 1.72 to 1.73.")

[What's New in OpenUI5 1.72](What_s_New_in_OpenUI5_1_72_521cad9.md "With this release OpenUI5 is upgraded from version 1.71 to 1.72.")

[What's New in OpenUI5 1.71](What_s_New_in_OpenUI5_1_71_a93a6a3.md "With this release OpenUI5 is upgraded from version 1.70 to 1.71.")

[What's New in OpenUI5 1.70](What_s_New_in_OpenUI5_1_70_f073d69.md "With this release OpenUI5 is upgraded from version 1.69 to 1.70.")

[What's New in OpenUI5 1.69](What_s_New_in_OpenUI5_1_69_89a18bd.md "With this release OpenUI5 is upgraded from version 1.68 to 1.69.")

[What's New in OpenUI5 1.68](What_s_New_in_OpenUI5_1_68_f94bf93.md "With this release OpenUI5 is upgraded from version 1.67 to 1.68.")

[What's New in OpenUI5 1.67](What_s_New_in_OpenUI5_1_67_a6b1472.md "With this release OpenUI5 is upgraded from version 1.66 to 1.67.")

[What's New in OpenUI5 1.66](What_s_New_in_OpenUI5_1_66_c9896e9.md "With this release OpenUI5 is upgraded from version 1.65 to 1.66.")

[What's New in OpenUI5 1.65](What_s_New_in_OpenUI5_1_65_0f5acfd.md "With this release OpenUI5 is upgraded from version 1.64 to 1.65.")

[What's New in OpenUI5 1.64](What_s_New_in_OpenUI5_1_64_0e30822.md "With this release OpenUI5 is upgraded from version 1.63 to 1.64.")

[What's New in OpenUI5 1.63](What_s_New_in_OpenUI5_1_63_e8d9da7.md "With this release OpenUI5 is upgraded from version 1.62 to 1.63.")

[What's New in OpenUI5 1.62](What_s_New_in_OpenUI5_1_62_771f4d5.md "With this release OpenUI5 is upgraded from version 1.61 to 1.62.")

[What's New in OpenUI5 1.61](What_s_New_in_OpenUI5_1_61_d991552.md "With this release OpenUI5 is upgraded from version 1.60 to 1.61.")

[What's New in OpenUI5 1.60](What_s_New_in_OpenUI5_1_60_5a0e1f7.md "With this release OpenUI5 is upgraded from version 1.58 to 1.60.")

[What's New in OpenUI5 1.58](What_s_New_in_OpenUI5_1_58_7c927aa.md "With this release OpenUI5 is upgraded from version 1.56 to 1.58.")

[What's New in OpenUI5 1.56](What_s_New_in_OpenUI5_1_56_108b7fd.md "With this release OpenUI5 is upgraded from version 1.54 to 1.56.")

[What's New in OpenUI5 1.54](What_s_New_in_OpenUI5_1_54_c838330.md "With this release OpenUI5 is upgraded from version 1.52 to 1.54.")

[What's New in OpenUI5 1.52](What_s_New_in_OpenUI5_1_52_849e1b6.md "With this release OpenUI5 is upgraded from version 1.50 to 1.52.")

[What's New in OpenUI5 1.50](What_s_New_in_OpenUI5_1_50_759e9f3.md "With this release OpenUI5 is upgraded from version 1.48 to 1.50.")

[What's New in OpenUI5 1.48](What_s_New_in_OpenUI5_1_48_fa1efac.md "With this release OpenUI5 is upgraded from version 1.46 to 1.48.")

[What's New in OpenUI5 1.46](What_s_New_in_OpenUI5_1_46_6307539.md "With this release OpenUI5 is upgraded from version 1.44 to 1.46.")

[What's New in OpenUI5 1.44](What_s_New_in_OpenUI5_1_44_a0cb7a0.md "With this release OpenUI5 is upgraded from version 1.42 to 1.44.")

[What's New in OpenUI5 1.42](What_s_New_in_OpenUI5_1_42_468b05d.md "With this release OpenUI5 is upgraded from version 1.40 to 1.42.")

[What's New in OpenUI5 1.40](What_s_New_in_OpenUI5_1_40_fbab50e.md "With this release OpenUI5 is upgraded from version 1.38 to 1.40.")

[What's New in OpenUI5 1.38](What_s_New_in_OpenUI5_1_38_f218918.md "With this release OpenUI5 is upgraded from version 1.36 to 1.38.")
