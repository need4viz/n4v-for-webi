# Navigation – N4V FOR WEBI Knowledge Base

Troubleshooting and how-to articles from the official [Need4Viz Support Knowledge Base](https://support.need4viz.com/kb/), category 4. Each entry gives the symptom, context and resolution; the full article with screenshots is linked below it. Back to the [Knowledge Base index](knowledge-base.md).

## Configuration of navigation feature

### Navigation elements work for some users but not for other

#### Symptom

- Need4Viz navigation element is working for some users but not for others

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz navigation element and use it to filter another bloc of the report
2. The navigation element is working
3. Save and close the Webi report
4. Another user open the webi report
5. The navigation element is not working

**Cause:**

- User has not the right to consume input controls (in Webi application).

#### Solution

A specific right as to be set for users in the CMC to enable Need4Viz navigation element functionality :

- Open the CMC
- Set the following rights on Webi application for the group of the user that cannot use Need4Viz navigation elements

[Full article](https://support.need4viz.com/kb/faq.php?id=12)

### Enable Need4Viz navigation for releases from 4.2 SP7 p5 to 4.2 SP8 p5

#### Symptom

- Need4Viz navigation element is not working : no interaction is done on the related Input Control when a selection is made in the navigation element

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : 4.2 SP7 p5 -> 4.2 SP8 p5
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure an Input Control to filter a bloc of the report
2. Create and configure a new Need4Viz navigation element to interact with this Input Control
3. When selecting a value in the navigation element, the Input Control is not updated (nothing changes)

**Cause:**

- In some releases of SAP BI, the technology used by Need4Viz to interact with Webi Input Controls has been modified by SAP. A specific setting has to be done in the CMC to activate this feature.

#### Solution

From versions 4.2SP7p6 to 4.2SP8p6, you need to enable an extension point on groups that need to use Need4Viz navigation element.

- Open the CMC
- Go to the users & groups window
- Right clic on the gorup and choose "Customization"

- In the panel, go to the "Extension" tab
- Select the "Extension Sample 1.0.0" and Save & Close

- Open a new BILaunchpad session et reopen the Webi report previously used
- A new Icon should appears on the bottom of the left rubber :

- The navigation is now available

[Full article](https://support.need4viz.com/kb/faq.php?id=16)

### Enable Need4Viz navigation for releases after 4.2 SP08 Patch 06

#### Symptom

- Need4Viz navigation element is not working : no interaction is done on the related Input Control when a selection is made in the navigation element
- Error message visible in the Chrome console : Cannot read properties of undefined (reading 'variable') or 'Not implemented yet...' or Cannot read properties of undefined (reading 'assignedDataObjects)
- Relative SAP Note : 2925234

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : 4.2 SP8 p6 -> ...
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure an Input Control to filter a bloc of the report
2. Create and configure a new Need4Viz navigation element to interact with this Input Control
3. When selecting a value in the navigation element, the Input Control is not updated (nothing changes)

**Error in the Chrome console:**

or

**Cause:**

- A change was made starting release 4.2 SP08 Patch 06 to enable navigation without enabling extension Points.

#### Solution

Update the Webi properties in the web application of SAPBI, by following this procedure :

1. Go to folder SAP BusinessObjects\tomcat\webapps\BOE\WEB-INF\eclipse\plugins\webpath.AnalyticalReporting\web\WEB-INF\classes
2. Edit webiviewer.properties and set ENABLE_EXTENSIONS_SERVICES=yes
3. Go to folder SAP BusinessObjects\tomcat\work\Catalina\localhost
4. Delete folder BOE
5. Restart Tomcat

If it was previously enabled, you can safely disable Extension Point. You can now use Need4Viz navigation components in your Webi reports.

[Full article](https://support.need4viz.com/kb/faq.php?id=17)

### Enable Need4Viz navigation for releases from 4.3 SP2+

#### Symptom

- Need4Viz navigation element is not working : no interaction is done on the related Input Control when a selection is made in the navigation element

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : 4.3 SP2+
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure an Input Control to filter a bloc of the report
2. Create and configure a new Need4Viz navigation element to interact with this Input Control
3. When selecting a value in the navigation element, the Input Control is not updated (nothing changes)

In the Console of the browser, the following error message is displayed :

**Cause:**

- In SAPBI 4.3SP2+, the Restful API used by N4V to interact with SAPBI are the ones served by the Tomcat (and not the WACS). But, by default, the Restful URL configured in the CMC is the WACS URL.

#### Solution

From versions 4.3SP2+, configure the Restful URL as relative path in the CMC (or explicitly use the Tomcat port and not the WACS port). As indicated in the installation guide of N4V for Webi :

[Full article](https://support.need4viz.com/kb/faq.php?id=64)

### Issue using N4V navigation in SAPBI 4.2 environment

#### Symptom

- Need4Viz navigation element is not working : no interaction is done on the related Input Control when a selection is made in the navigation element
- Following error message is displayed in the Chrome console when trying to update a Webi variable through an N4V navigation component : Cannot read properties of undefined (reading 'variable') or 'Not implemented yet...' or Cannot read properties of undefined (reading 'assignedDataObjects) :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : 4.2 SP8 p6 ->
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure an Input Control to filter a bloc of the report
2. Create and configure a new Need4Viz navigation element to interact with this Input Control
3. When selecting a value in the navigation element, the Input Control is not updated (nothing changes)

**Cause:**

**An additional configuration in SAPBI is necessary to enable navigation usage in N4V components.**

**See the related article : [https://www.need4viz.com/support/kb/faq.php?id=17](https://www.need4viz.com/support/kb/faq.php?id=17)**

[Full article](https://support.need4viz.com/kb/faq.php?id=78)

## Setting and usage

### How to configure a Need4Viz navigation element

#### Symptom

- Configure a Need4Viz navigation element

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : all versions

#### Resolution

To configure a Need4Viz navigation element :

1. Open a new Webi document an insert a Webi table (For example, Webi based on eFashion univers, get objects State, Year, Quarter, Sales revenues)
2. Insert a Need4Viz component (ex. Drillbar) with the same elements as the Webi table
3. Create a simple list-type Webi input control on the "Quarter" dimension
4. Give a name (must be unique throughout the Webi report) to this control, here "N4V_IC1_Quarter"
5. Select the report components to control (here the Webi table and the Need4Viz Drillbar)
6. Save the document (so that the input control is created in the Webi report and thus becomes controllable via the Need4Viz components)
7. Insert a Need4Viz navigation element (ex. Simple list of values) based on the same dimension as that of the previously created input control
8. Open the Format Custom Element panel
9. (Optional) In the "Values" tab, check the box to add an "All values" at the top of the list, you can also modify the wording of this new choice in the list
10. In the "Input_control" tab, enter the name of the Webi input control previously created (unique name throughout the Webi report)
11. The choice in the list of the element Need4Viz now acts on the 2 Webi blocks (as well as on the Webi input control whose shutter can now be folded)
12. Likewise, the choice of the value "All values" makes it possible to select all the values

#### Attachments

- French documentation : [Use_Navigation_Elements_FR.pdf](https://support.need4viz.com/documents/Use_Navigation_Elements_FR.pdf)
- English documentation : [Use_Navigation_Elements_EN.pdf](http://www.need4viz.com/documents/Use_Navigation_Elements_EN.pdf)

[Full article](https://support.need4viz.com/kb/faq.php?id=11)

### Use Input Control filter in whole report except on Need4Viz navigation elements

#### Symptom

- Create a Webi report with blocs and an Input Control on the whole report
- Configure a Need4Viz navigation element based on that Input Control

- When you choose an item in the navigation element, the bloc is correctly filtered but the navigation element is itself filtered

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : all versions

#### Cause

- The Need4Viz component is considered by Webi engine like any other bloc. So when the Input Control is activated on the whole report, the Need4Viz component is filtered too.
- From Need4Viz engine side, the data sent by Webi are already filtered so the engine cannot apply a like NoFilter option.
- The NoFilter() cannot be used in the object definition used in the navigation element because this Webi function can only be applied on a measure (not a dimension)

#### Resolution

There are 2 ways to configure a Need4Viz navigation element to not be filtered by a Webi Input Control :

**1/ Throught the Input Control perimeter**

- do not activate the Input Control on the whole report

- but only on each individual blocs/charts you want to be filtered excepeted the Need4Viz navigation element

**2/ Use a specific query for the list of values**

- As the Need4Viz navigation elements just send selected value(s) to an Input Control (and not read information from the Input Control to build it's own list of values), an individual query that just give all the list of values can be used to feed the Need4Viz navigation elements. Example :
- Define a main query with dimensions and measures. "Year" is one of the dimensions
- Build a bloc with the data and an Input control based on the "Year" dimension
- Affect the Input Control to the whole report
- Build a new query to retrieve only "Year" dimension
- **Do not merge the "Year" dimension between the 2 queries**
- Build a Need4Viz Navigation Simple List based on the "Year" dimension of the second query and affect it to the Input Control -> when selecting a year in the navigation element, the bloc is filtered correctly and all the year values still remains in the Need4Viz element

[Full article](https://support.need4viz.com/kb/faq.php?id=18)

### Native webi link element does not work on merged dimensions object

#### Symptom

- Create a Webi report with at least 2 queries
- Merge 2 dimensions based on 1 object from each query
- Configure a Need4Viz chart based on the merged object (or on 1 object used in the merge)
- Define the native Webi link element feature on the chart (filter another Webi block)

- When you click on the chart to filter the Webi block, nothing happen.

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : all versions

#### Cause

- The Need4Viz component needs the merged dimension name to be the same as the object used in the compenent (and defined in the native Webi link element feature).

#### Resolution

Rename the merge dimension with the same name as the dimension used in the Need4Viz component.

**1/ Example of merged dimensions with a different name :**

- In this case, if you use one of those dimensions in a Need4Viz component, the native Webi linking element will not work :
- create a Need4Viz chart and assign a merged dimension as an input dimension
- Then define a native Webi link element :
- **-> The filtering does not work**

**2/ Example of merged dimensions with a correct name :**

- In this case, if you use one of those dimensions in a Need4Viz component, the native Webi linking element will work :
- rename the merged dimension with the same name as the dimension used in the Need4Viz chart :
- **-> The filtering works**

[Full article](https://support.need4viz.com/kb/faq.php?id=26)

### Navigation elements / elements linking are not working in FIORI portal in SAP BI 4.2 to 4.3 SP01

#### Symptom

- Create a Webi report and add block that you want to filter using navigation components or element linking
- Create an Input Control
- Fill the input control Name in the Control section of the Need4Viz navigation element
- Or Define the native Webi link element feature on the chart (filter another Webi block)
- When you click on the chart to filter the Webi block or in the navigation element, nothing happens.

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions till 4.3 SP01
- Need4Viz : all versions

#### Cause

- The navigation features with Need4Viz component are not yet available in the FIORI Portal.

#### Resolution

This is planned to be available starting with version 4.3 SP02 (it is subject to be changed). It is not planned to be available in the FIORI's portal for versions 4.2 and also not in version 4.3 prior to the SP02

[Full article](https://support.need4viz.com/kb/faq.php?id=32)

### How to create a Checkboxes element with custom list of values to affect a Webi variable

#### Symptom

- Create a Checkboxes selection list based on a Custom list of values.
- Affect the result of the selection in a Webi variable.

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : all versions

#### Procedure

- Create a Webi report with bloc
- Create a "Dummy" variable (="x")
- Create a "Result" variable
- Create the Checkboxes element with the Dummy variable as input
- Set the element as following
- Now you can select all values in your list
- only some values
- or none value
- and get the correct result in the Result variable.

[Full article](https://support.need4viz.com/kb/faq.php?id=34)

### How to configure a Need4Viz navigation element in SAPBI 4.3SP2+

#### Symptom

- Configure a Need4Viz navigation element

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.3SP2+ Webi versions
- Need4Viz : all versions

#### Resolution

To configure a Need4Viz navigation element :

1. Open a new Webi document an insert a Webi table (For example, Webi based on eFashion univers, get objects State, Year, Quarter, Sales revenues)
2. Insert a Need4Viz component (ex. Drillbar) with the same elements as the Webi table
3. Activate the FIlter bar :
4. Create a simple list-type Webi input control on the "Quarter" dimension :
5. Give a name (must be unique throughout the Webi report) to this control, here "N4V_IC1_Quarter"
6. Select the report components to control (here the Webi table and the Need4Viz Drillbar)
7. Save the document (so that the input control is created in the Webi report and thus becomes controllable via the Need4Viz components)
8. Insert a Need4Viz navigation element (ex. Radio Button) based on the same dimension as that of the previously created input control
9. Open the Format Custom Element panel
10. (Optional) In the "Values" tab, check the box to add an "All values" at the top of the list, you can also modify the wording of this new choice in the list
11. In the "Input_control" tab, enter the name of the Webi input control previously created (unique name throughout the Webi report)
12. The choice in the list of the element Need4Viz now acts on the 2 Webi blocks (as well as on the Webi input control whose shutter can now be folded)
13. Likewise, the choice of the value "All values" makes it possible to select all the values

In Design mode, to enable the Custom Element Interaction, activate the display mode :

[Full article](https://support.need4viz.com/kb/faq.php?id=44)

### Making a cascading N4V list of values controls

#### Symptom

- Create two linked lists of values.

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3 Webi versions
- Need4Viz : all versions

#### Procedure

- Create a Webi report with a bloc containing 2 linked dimensions. In the following example we have the name of the buses stations and the status of the station
- Create an Input Control (simple list of values) based on the name and affect it to the Webi bloc
- Create an Input Control (simple list of values) based on the status and affect it to the Webi bloc
- Create a N4V List of value based on the name, add "all values" and affect it the "name" Input Control
- Create a N4V List of value based on the status, add "all values" and affect it the "status" Input Control
- Update the Input Control based on the status and affect the N4V List "name" bloc to it
- In the global settings of the N4V list status, tick the reset "Input Controls when selection is done" :   If you want to only reset the IC based on the name (and not all your report IC), just set it as :   And now, by filtering the first list, we filter the block and the second list :   By filtering then in the second, we filter the block :   Selecting a value from the first list resets the second list :

[Full article](https://support.need4viz.com/kb/faq.php?id=47)

### How to create a Calendar picker and use it your Webi report

#### Symptom

- Create a calendar picker.
- Affect the result of the selection in a Webi variable.
- Use this variable as a filter

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 & 4.3 Webi versions
- Need4Viz : all versions

#### Procedure

The following example is gived for a range of 2 selected dates. The same behavior can be achieved for only 1 date selection.

- Create a Webi report with bloc
- Create an empty "Date_From" variable
- Create a second emply "Date_To" variable
- Create the Calendar Picker element with the "Date_From" and "Date_To" variables as input
- If you need to filter your report based on days, set the element as following (change if you need to filter based on another kind of period) :
- Now you can select your dates in the calendar, it will affect the variables :

- Now you can add a filtered variable in your Webi report :
- then you can filter your different report elements with the created filtered variable :

Depending on the kind of period selected (days, months, time...), the result sent to the Webi variables will be formated differently :

- Day → YYYY-MM-DD
- DayTime → YYYY-MM-DD**T**HH:MI
- Time → HH:MI
- Month → YYYY-MM
- Week → YYYY-**W**WK

[Full article](https://support.need4viz.com/kb/faq.php?id=69)

### How to use a N4V navigation element interacting in the whole Webi document

#### Symptom

- Create a Webi document with at least 2 reports (sheets)
- Create a Webi Input Control based on the entire document
- Insert a N4V navigation element (for instance, a dropdown list) on one of the Webi reports.
- Affect the N4V navigation element to the Input Control.
- When selecting a value in the dropdown list, the Input Control is not affected.

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3 Webi versions
- Need4Viz : all versions

#### Cause

The Webi features used by N4V elements to interact with Input Control are not yet implemented by SAP to interact with Document Input Controls.

#### Resolution

Using a N4V navigation element interacting with the whole document is possible by controlling a Webi variable instead of an Input Control.

***1. For a single value selector (list, radio button...)***

- Create a Webi variable (for instance "V_State" content ="") and affect the control of the N4V element to this Webi variable :
- Create a second Webi variable to compare the dimension value with the result of the controled variable (containing "=[dim]=[V_dim]") :
- Use this variable to filter all the Webi blocs or entire reports in the document (filter on the "1" value) :

***2. For a multi values selector (multi list, checkboxes...)***

- The scheme is approximately the same as previously :
- Create a Webi variable (for instance "VCode" content ="") and affect the control of the N4V element to this Webi variable
- Create a second Webi variable to test if the value of [Code] is in the selected list [VCodes], the formula is **=Pos([VCodes];[Code])**. If the return is >0, then the value is in the list.
- Use this variable to filter the reports elements in the whole document.

[Full article](https://support.need4viz.com/kb/faq.php?id=77)

### How to create a popup filters with multi N4V navigation elements in a Webi report

#### Symptom

- Create a popup with multiple N4V navigation elements.

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3 Webi versions
- Need4Viz : all versions

#### Procedure

- Create a Webi report with a bloc to filter and 2 (or more) N4V navigation element. For instance, here, one list on State and one checkbox on Year :
- Insert a standard blank cell on the report and customize it (as it will be the background of your popup) :
- Set the Order of the blanck cell to the Back :
- Create a Webi variable which contain a static value (for instance "v_Menu_button" = "Popup") :
- Create a second Webi variable which contain a static value (for instance "v_Menu_button" = "Popup") :
- Insert a Menu button N4V element, and assign the "v_Menu_button" variable as input data. Define the v_Closed_Popup variable as the control :
- Insert a N4V Reset Button (used to close the popup) and affect "None" input control option and the "v_Closed_Popup" with a reset value "true" :
- For all the N4V navigation elements and the blank Webi cell (background of the popup), tick the "Hide when following formula is true" and enter the formula =[v_Closed_Popup]="true" :
- Position all N4V elements on the blanck Webi cell and send them to the Front :
- Now when you click on "Close", the popup is hidden :
- When you click on "Popup", the popup is displayed :

[Full article](https://support.need4viz.com/kb/faq.php?id=84)

### How to use a date/time object in a N4V navigation element

#### Symptom

- You need to use date/datetime values to filter your webi report through a N4V navigation element (dropdown list, radio buttons, checkboxes...) but it doesn't work

#### Environment

- Need4Viz : all versions
- SAPBI : all versions

#### Symptom

Create a query with a date/datetime dimension and mesure(s) then display the result in a Webi table.

Create an Input Control based on the date/datetime object.

Create a N4V navigation element (dropdown list) assign the date/datetime object and affect the created Input Control.

When you select a value in the N4V element, the Input Control is not updated and the report is not filtered.

This behavior is due to a limitation in Webi that cannot send "date/datetime" object to N4V engine in the expected format.

#### Resolution

To use a date/datetime object as a filter, you just need to create a corresponding text variable and use it to filter your report.

Creation of the Webi variable :

Creation of the Input Control

Using Webi variable in the N4V navigation element

Filtering the table

[Full article](https://support.need4viz.com/kb/faq.php?id=120)

## Unexpected behaviour

### Selection in a navigation component is not correctly print when exporting report in PDF/XLS

#### Symptom

- Configure a Need4Viz navigation element (for instance, a list element)
- Make a selection in the list in Webi
- Export the rendered report in PDF/XLS
- The report exported is correctly filtered but the selected item is not displayed in the exported navigation element)

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 & 4.3 Webi versions
- Need4Viz : all versions

#### Cause

The selection made in a navigation element in Webi is done in the user's browser session but cannot be transmitted to N4V engine when the Webi export is done (PDF/XLS). When the N4V engine export the navigation element in PNG format to send it to Webi (the PNG will be included in the final PDF/XLS export of the full report), the default value of the navigation element is selected (and not the selected value done in Webi).

#### Workaround

We are currently working with SAP Webi team to try to find a solution on this behaviour but for now the only workaround that can be proposed is the following one :

- Create in the dashboard a cell containing a summary of the selected values (for each N4V navigation element)
- In the **Extended parameters** of the navigation element, check the "**Global / Hide component during pdf/xls export**" :

When the report is exported, the navigation element is hidden and only the summary of the selected value is shown.

We are working with SAP team about another trouble with this workaround : the hidden N4V navigation element is replaced by a white frame (instead of a transparent or empty frame).

[Full article](https://support.need4viz.com/kb/faq.php?id=93)
