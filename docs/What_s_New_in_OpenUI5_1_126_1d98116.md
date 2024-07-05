<!-- loio1d981160daf94bbfb0324311f1b35716 -->

| loio |
| -----|
| 1d981160daf94bbfb0324311f1b35716 |

<div id="loio">

view on: [demo kit nightly build](https://sdk.openui5.org/nightly/#/topic/1d981160daf94bbfb0324311f1b35716) | [demo kit latest release](https://sdk.openui5.org/topic/1d981160daf94bbfb0324311f1b35716)</div>

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

## What's New in OpenUI5 1.126

With this release OpenUI5 is upgraded from version 1.125 to 1.126.

> ### Note:  
> Content marked as <span style="color:#666666;"><span class="SAP-icons-V5"></span></span>**[Preview](https://help.sap.com/docs/whats-new-disclaimer)** is provided as a courtesy, without a warranty, and may be subject to change. For more information, see the [preview disclaimer](https://help.sap.com/docs/whats-new-disclaimer).

****


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

Upcoming 

</td>
<td valign="top">

Deleted 

</td>
<td valign="top">

Announcement 

</td>
<td valign="top">

**End of Cloud Provisioning for OpenUI5 Versions \(Q2/2024\)** 

</td>
<td valign="top">

**End of Cloud Provisioning for OpenUI5 Versions \(Q2/2024\)**

> ### Note:  
> The following information concerns important upcoming changes for end users. These changes may require end users to adjust and/or test cases to be adapted, but they won't stop or disrupt software or processes.

The following OpenUI5 versions will be removed from the OpenUI5 Content Delivery Network \(CDN\) after the end of Q2/2024.

**Minor Versions Reaching Their End of Cloud Provisioning**

The following versions including all patches will be removed entirely:

-   1.111
-   1.112
-   1.113
-   1.115

**Action**: Upgrade to a version that is still in maintenance.

**Patch Versions Reaching Their End of Cloud Provisioning**

The following patches will be removed:

-   Long-term maintenance versions:

    -   1.38.61
    -   1.71.55-1.71.56
    -   1.84.32 to 1.84.35
    -   1.96.18 to 1.96.20
    -   1.108.7 to 1.108.14

    **Action**: Upgrade to the latest available patch for the respective OpenUI5 version.


For more information, see [Version Overview](https://sdk.openui5.org/versionoverview.html).

<sub><span style="color:#666666;"><span class="SAP-icons-V5"></span></span>**[Preview](https://help.sap.com/docs/whats-new-disclaimer)**•Deleted•Announcement•Info Only•Upcoming</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

9999-01-01

</td>
</tr>
<tr>
<td valign="top">

1.126 

</td>
<td valign="top">

Changed 

</td>
<td valign="top">

Control 

</td>
<td valign="top">

**`sap.m.Avatar`** 

</td>
<td valign="top">

**`sap.m.Avatar`**

-   You can now add badges without requiring a press event.

-   When the `sap.m.Avatar` with a badge is in focus, the `badgeTooltip` is now announced by screen readers.


<sub>Changed•Control•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
<tr>
<td valign="top">

1.126 

</td>
<td valign="top">

Changed 

</td>
<td valign="top">

Control 

</td>
<td valign="top">

**`sap.m.InputBase`** 

</td>
<td valign="top">

**`sap.m.InputBase`**

We have exposed the `setPreferredUserInteraction` method to allow application developers to set the preferred interaction type for the input controls. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.m.InputBase). 

<sub>Changed•Control•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
<tr>
<td valign="top">

1.126 

</td>
<td valign="top">

Changed 

</td>
<td valign="top">

Control 

</td>
<td valign="top">

**`sap.m.RadioButton`** 

</td>
<td valign="top">

**`sap.m.RadioButton`**

The control now supports wrapping. By default, the wrapping is disabled, and the label text is truncated without hyphenation. You can control its behavior using the new `wrapping` and `wrappingType` properties. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.m.RadioButton) and the [Sample](https://sdk.openui5.org/entity/sap.m.Carousel/sample/sap.m.sample.RadioButton).

<sub>Changed•Control•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
<tr>
<td valign="top">

1.126 

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

-   We have added a new `displayZeroValue` property to the \(experimental\) StackedBar micro chart. When set to `true` \(default\), each bar of the chart is displayed, even if its corresponding value is zero. For more information, see the [Card Micro Charts](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/learn/features/microcharts) section and the [Sample](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/explore/microCharts/stackedBarZeroValues) in the Card Explorer.

-   We have added a new `fitType` property to the icons in List and Table cards. Using the new property, you can now control how the image fits in the available icon space. For more information, see the [List Card Charts](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/learn/typesDeclarative/list) and the [Table Card](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/learn/typesDeclarative/table) sections in the Card Explorer.

-   We have \(experimentally\) enhanced the responsive behavior of the cards. For more information, see the [Sample](https://sdk.openui5.org/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/explore/progressive) in the Card Explorer.


<sub>Changed•Control•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
<tr>
<td valign="top">

1.126 

</td>
<td valign="top">

Changed 

</td>
<td valign="top">

Feature 

</td>
<td valign="top">

**OpenUI5 OData Models** 

</td>
<td valign="top">

**OpenUI5 OData Models**

We have adapted the calculation of the `$top` and `$skip` query options for both the `sap.ui.model.odata.v2.ODataModel` and the `sap.ui.model.odata.v4.ODataModel` so that more data is requested when scrolling in a list. These requests now typically have a `$top` value that corresponds to the threshold parameter set for the `sap.ui.table.Table` control.

For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.table.Table%23controlProperties).

<sub>Changed•Feature•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
<tr>
<td valign="top">

1.126 

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

-   When you use the experimental selection feature, a `selectionChanged` event is now raised by the `sap.ui.model.odata.v4.ODataListBinding` if the selection is either changed via `sap.ui.model.odata.v4.Context#setSelected` or by changing the value of the `@$ui5.context.isSelected` client-side annotation.

    For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.model.odata.v4.ODataListBinding%23events/selectionChanged).

-   We have provided the experimental `createInPlace` parameter for the `$$aggregation / sap.ui.model.odata.v4.ODataListBinding#setAggregation` binding parameter. When set, newly created nodes are shown in the back-end position and not in first position among their siblings.

    For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.model.odata.v4.ODataListBinding%23methods/setAggregation).

-   As an experimental feature, we now allow `OneWay` property bindings for structural properties that have a complex type. Certain restrictions apply.

    For more information, see [Property Binding With an Object Value](Initialization_and_Read_Requests_fccfb2e.md#loiofccfb2eb41414f0792c165e69a878717__section_PBOV).


<sub>Changed•Feature•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
<tr>
<td valign="top">

1.126 

</td>
<td valign="top">

Deprecated 

</td>
<td valign="top">

Feature 

</td>
<td valign="top">

**Deprecations** 

</td>
<td valign="top">

**Deprecations**

There are currently no major deprecations. For a complete list of all deprecations, see [Deprecated APIs](https://sdk.openui5.org/api/deprecated).

<sub>Deprecated•Feature•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
<tr>
<td valign="top">

1.126 

</td>
<td valign="top">

Changed 

</td>
<td valign="top">

Control 

</td>
<td valign="top">

**`sap.ui.mdc.Table`** 

</td>
<td valign="top">

**`sap.ui.mdc.Table`**

We have now added keyboard support for reordering columns in this control. The reordering is done using drag and drop, which is why the keyboard support is offered via the aggregations of the drag and drop implementation. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.ui.core.dnd.DragDropBase%23methods/setKeyboardHandling). 

<sub>Changed•Control•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
<tr>
<td valign="top">

1.126 

</td>
<td valign="top">

Changed 

</td>
<td valign="top">

Control 

</td>
<td valign="top">

**`sap.m.table.columnmenu.Menu`** 

</td>
<td valign="top">

**`sap.m.table.columnmenu.Menu`**

We have adapted the entities of the `sap.m.table.columnmenu` class: The `IColumnHeaderMenu` interface is now no longer experimental and offers some new methods and events. We have also improved the documentation and provided a new sample with a custom column menu. For more information, see the [API Reference](https://sdk.openui5.org/api/sap.m.table.columnmenu.MenuBase) and the [Sample](https://sdk.openui5.org/entity/sap.m.Table/sample/sap.m.sample.TableIColumnHeaderMenu).

<sub>Changed•Control•Info Only•1.126</sub>

</td>
<td valign="top">

Info Only 

</td>
<td valign="top">

2024-07-11

</td>
</tr>
</table>
