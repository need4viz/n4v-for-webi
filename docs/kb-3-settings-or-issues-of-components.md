# Settings or issues of components – N4V FOR WEBI Knowledge Base

Troubleshooting and how-to articles from the official [Need4Viz Support Knowledge Base](https://support.need4viz.com/kb/), category 3. Each entry gives the symptom, context and resolution; the full article with screenshots is linked below it. Back to the [Knowledge Base index](knowledge-base.md).

## Color Palettes

### How to add custom palette in the list available in Need4Viz components using a palette of color

#### Symptom

- Add one (or more) custom palette(s) available in all Need4Viz components using a palette

#### Environment

- Windows Server / Linux
- Need4Viz : versions >= 2021.4.1

#### Resolution

To add custom palette of color:

1. Define the list of all the colors that will compose your palette. The colors need to be defined in HEX (#RRGGBB) format. Respect the exact syntax formatting of the list. For instance, the following list of colors will be use in our example: The corresponding list of colors for this palette is: **['#542e71','#fb3640','#fdca40','#a799b7']**. You can add as many colors as possible you want in the palette. If enough colors are not available in the palette when using it in a component, Need4Viz will generate random colors to complete the palette for this component.
2. On each Need4Viz server, open the file ***~******Need4Viz_folder_installation\*****nodejs\node_modules\custom_element\ce_lib\resources\list_palettes.js**
3. Add your list of color and give a codename to the list, for instance in our example pal05 is defined (**respect the exact syntax, the codename mustn't start with a number**) :
4. Save the file
5. Open the file ***~******Need4Viz_folder_installation\*****nodejs\node_modules\custom_element\ce_settings\lang_EN\****_list_palettes.json**.
6. Add the new entry for your palette. Report in the "id" field the codename defined previously. You can choose the name you want (this name will be displayed in the list of values of each Need4Viz component) :
7. Report exactly the same entry in the FR version file ***~******Need4Viz_folder_installation\*****nodejs\node_modules\custom_element\ce_settings\lang_FR\****_list_palettes.json**.
8. Stop and restart the Need4Viz server by launching the Need4Viz_stop.ps1 and Need4Viz_start.ps1 scripts in a PowerShell window.
9. Open a Need4Viz component that use color palettes and in the Extended parameters/Global, check your entry is added :
10. Choose the new palette and confirm it is correctly used:

#### 

#### Caution

The use of custom files needs to respect exactly the instruction and structure mentioned above.

The JSON file must be encoded in UTF-8.

[Full article](https://support.need4viz.com/kb/faq.php?id=30)

### How to add custom palette in the list available in Need4Viz components using a second palette of color

#### Symptom

- Add one (or more) custom palette(s) available in Need4Viz components using a second custom palette list

#### Environment

- Windows Server / Linux
- Need4Viz : versions >= 2021.7.2
- Need4Viz components -> Maplines / Drillmap (subdivision colors), Pie in pie (second disc colors)

#### Resolution

To add custom palette of color :

1. Define the list of all the colors that will compose your palette. The colors need to be defined in hexa format. Respect the exact syntax formatting of the list. For instance, the following list of colors will be use in our example : The corresponding list of colors for this palette is : **['#542e71','#fb3640','#fdca40','#a799b7']**. You can add as many colors you want in the palette. If not enough colors are available in the palette when using it in a component, Need4Viz will generate random colors to complete the palette for this component.
2. On each Need4Viz server, open the file ***~******Need4Viz_folder_installation\*****nodejs\node_modules\custom_element\ce_lib\resources\list_palettes.js**
3. Add your list of color and give a codename to the list, for instance in our example pal05 is defined (respect the exact syntax) :
4. Save the file
5. Open the file ***~******Need4Viz_folder_installation\*****nodejs\node_modules\custom_element\ce_settings\lang_EN\****_list_palettes_divmaps.json**.
6. Add the new entry for your palette. Report in the "id" field the codename defined previously. You can choose the name you want (this name will be displayed in the list of values of each Need4Viz component) :
7. Report exactly the same entry in the FR version file ***~******Need4Viz_folder_installation\*****nodejs\node_modules\custom_element\ce_settings\lang_FR\****_list_palettes_divmaps.json**.
8. Stop and restart the Need4Viz server by launching the Need4Viz_stop.ps1 and Need4Viz_start.ps1 scripts in a PowerShell window.
9. Open a Need4Viz component that uses second color palettes (ex. Pie in pie) and in the Extended parameters/Options, check your entry is added :
10. Choose the new palette and check it is correctly used for the second pie :

#### 

#### Caution

The use of custom files needs to respect exactly the instruction and structure mentionned above.

The json file must be encoded in UTF8.

[Full article](https://support.need4viz.com/kb/faq.php?id=52)

### Specific Webi palette is not kept after a changing data assignment

#### Symptom

- When modifying an object in a N4V component where a specific Webi palette is used, the default "Belize" Webi palette is used (instead of the previous specified)

#### Environment

- SPABI 4.2 & 4.3
- Need4Viz : all version

#### Reason and Prerequisites

**Steps To Reproduce:**

To set a specific Webi palette of color :

1. Insert in a Webi report a N4V component (for instance a Variable Pie) with a dimension an a measure
2. Change the Webi palette (default is "Belize") and choose a specific one ("Spectrum") and apply
3. Go back to the Data Assignment and change the measure
4. Apply and see the colors are changed (default Webi palette is used instead of "Spectrum")

**Cause:**

This behaviour is caused by a defect in Webi that doesn't keep it's correct palette set.

**Fix:**

This issue is fixed in SAP **BI 4.3 SP4 p5+** => See the SAP Note [https://me.sap.com/notes/3284282/E](https://me.sap.com/notes/3284282/E)

[Full article](https://support.need4viz.com/kb/faq.php?id=75)

### Creating a new custom Webi palette hanging Webi indefinitely

#### Symptom

- When creating a custom Webi palette in a N4V component, the cursor is hanging indefinitely

#### Environment

- SAPBI 4.2
- Need4Viz : all version

#### Reason and Prerequisites

**Steps To Reproduce:**

To create a custom Webi palette of color :

1. Insert in a Webi report a N4V component (for instance a Variable Pie) and change the default Webi palette to "Custom"
2. Click on "new", the cursor is hanging indefinitely
3. Press Escape to quit the hanging mode

**Cause:**

This behaviour is caused by a defect in Webi.

**Workaround:**

To create a custom palette, you must select an existing one before clicking on "New". For instance, select the "Belize" palette then click on "New" :

Then you can create your own palette :

[Full article](https://support.need4viz.com/kb/faq.php?id=76)

## Common features

### How to copy to Excel the data used in any N4V widget

#### Symptom

- Simply way to copy/paste to Excel the data used in any N4V Widget (Webi dataset)

#### Environment

- Windows Server / Linux
- Need4Viz : all versions

#### Resolution

The best and easy way to copy/paste to Excel all the data used in any N4V Widget, is the following :

- In the Extended Parameter, in the Menu category, Add the Table Data button :
- Now in the corner of the Widget, you can see the N4V Menu burger  (if more than one feature is available) or just the Data Table View icon
- Open the Data Table View and clic on the 3 vertical point behind any label of the header :
- In the menu displayed, clic on "Copy data":
- As soon as data is copied in the clipboard, a message is displayed during few seconds:
- Now you can open an Excel workbook and press Ctrl+V in a new tab:

Data is copied without any formating so you can use your measures directly in Excel.

[Full article](https://support.need4viz.com/kb/faq.php?id=111)

### How to quickly save on your laptop a full HTML file of any N4V Widget

#### Symptom

- Simply way to save on your laptop the full HTML rendering of any N4V Widget

#### Environment

- Windows Server / Linux
- Need4Viz : all versions

#### Resolution

The best and easy way to save locally a full HTML file of any N4V Widget is the following:

- Open your Webi report containing N4V widgets in a Chrome session (the maner can be transposed to any other browser)
- Move the mouse inside the N4V widget and right-clic (in 4.3, do this action in "Reading" mode):
- In the contextual menu, select the "View frame source"
- A new tab is opened in your browser, displaying all the HTML code of the widget:
- Select all the HTML code (Ctrl+A), then copy it in the clipboard (Ctrl+C)
- Open any text editor (Notepad, Notepad++...) and paste the clipboard content to a new file
- Save the file locally on your laptop with an .html extension:
- Now you can double clic on the html file it will be opened in your browser and you'll can see the full N4V widget outside of Webi:

[Full article](https://support.need4viz.com/kb/faq.php?id=112)

### How to export your Webi report in a lcmbiar to send it to Need4Viz support

#### Symptom

- Simply way to generate a lcmbiar of your Webi report containing N4V widget and send it to Need4Viz Support

#### Environment

- Windows Server / Linux
- Need4Viz : all versions
- SABI : all versions

#### Resolution

Before générating a lcmbiar with your Webi report, please be sure that :

- Your Webi report is saved **WITH THE DATA** (the support team will not be able to refresh it)
- The report is saved with the "Refresh on open" parameter unchecked :

**To generate your lcmbiar**

Open your SAPBI CMC Portal (as administrator or with a user having the capability to generate a lcmbiar) and select "Promotion Management"

Click on "New Job"

Enter your company name and date in the Name field :

Select the Source of the lcmbiar ("Login to New CMS")

Select your source system (generally : localhost:6400) and "login"

In the Destination, choose "Output to LCMBIAR File" (check a green tick is displayed on the Source line) :

Click on "Create"

In the popup newly opened, select the Webi report you want to add in the lcmbiar (navigate in the left folders tree)

Click on "Add & Close"

Once the popup is closed, click on "Promote"

A new popup is displayed

Uncheck the "Password Encryption" (or if you want the lcmbiar to be crypted by a password, fill it and give it to the Need4Viz Support when you send them the lcmbiar otherwise they will not be able to open it)

Then click on Export to generate the lcmbiar :

You can retrieve the lcmbiar in your download folder on your laptop.

[Full article](https://support.need4viz.com/kb/faq.php?id=115)

### How to fix the color of each value of a dimension in the N4V widgets

#### Symptom

- You want to assign a specfic color for each value of a dimension in a N4V widget

#### Environment

- Windows Server / Linux
- Need4Viz : all versions (depending on the feeding of the N4V widget). Widgets -> Drillbar, MultiChart, MultiDrill, Pie in Pie, Sunburst,...

#### Resolution

Generally speaking, in the N4V widgets, when multi measures are provided in input, the color of each measure is affected by the selected palette (1st color of the palette -> 1st measure, 2nd color -> 2nd measure...). When only one measure is provided, either the chart is monocolor (the first color of the palette is selected or depending on the settings, you can select a specific color) either you can draw a multicolor chart. In this case, the color affected to the values of input dimension is provided by the selected palette (1st color of the palette -> 1st value of the dimension, 2nd color -> 2nd value of the dimension...)

Technically, it's not possible to affect a specific color to a specific value of the dimensions through the settings of the widget (Extended Parameters).

But to enable this possibility, we have progressively added a new way to specify a color for dimension value, through the "Data feeding" of some widgets.

When a widget offers this way, you'll find in the Data Feeding, a specific field (generally named "Color") :

The object sent to the field "Color" must return a specific color in RGB format.

You can use a Webi variable to affect a specific RGB color for each different values of your dimension (and provide a default color for the non affected values).

For instance, the following kind of variable can be used (color is specified for each value of the [TYPE] dimension object :

RGB colors in hexa are always formatted as : '#' + 2 digits for the Red color + 2 digits for the Green color + 2 digits for the Blue color. In some case, you can add additional 2 digits for the opacity.

You can use the N4V Palette Panel to choose your colors, and get the corresponding RGB hexa code :

You can also use the N4V Settings Panel and any color picker setting to choose your color (and get the RGB hexa code) :

[Full article](https://support.need4viz.com/kb/faq.php?id=123)

## Data Analyzer

### Issue when displaying Extended Pivot Table (blocking in Analyzing data...)

#### Symptom

- Configure a Need4Viz Extended Pivot Table. The following popup is continuously running :
- In the console of Chrome (F12), you can get the following kind of errors :

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3 Webi versions
- Need4Viz : all versions

#### Resolution

The N4VCustomElements webapp is deployed on a separate web server of the BOE/BI Tomcat (or the URL provided in the config.js file is not the same as the BOE/BI server URL. This generate a CORS Policy issue in the browser.

To avoid that, you need to configure the webapplication server hosting the N4VCustomElements webapp to allow the the cross origin for the specified domains accessing the N4VCustomElements webapp.

N4V webapp hosted on an Apache server :

1. The N4VCustomElement webapp is served by an Apache server (SERVER A)
2. The BOE webapp is installed on a Tomcat server (SERVER B)
3. The BOE webapp is accessible from outside company through the URL **`https://subdomain1.domain1.com`**
4. The BOE webapp is accessible from inside company through the URL **`https://subdomain2.domain2.com`**
5. The BOE webapp is also accessible from inside company directly on the Tomcat server through URL **`http://serverB.domain3.net:8080`**
6. In the httpd.conf of the SERVER A, configure the headers_module as following :
  1. check the line is uncommented : **LoadModule headers_module modules/mod_headers.so**
  2. Add the following entry :

N4V webapp hosted on an Tomcat server :

1. The N4VCustomElement webapp is served by a Tomcat server (SERVER A)
2. The BOE webapp is installed on a Tomcat server (SERVER B)
3. The BOE webapp is accessible from outside company through the URL **`https://subdomain1.domain1.com`**
4. The BOE webapp is accessible from inside company through the URL **`https://subdomain2.domain2.com`**
5. The BOE webapp is also accessible from inside company directly on the Tomcat server through URL **`http://serverB.domain3.net:8080`**
6. Activate the CorsFilter in the **tomcat/conf/web.xml** file of the Server A :
7. Change the "*" cors.allowed.origins with the list (separated by commas) of URLs used to access your SAPBI instance, Ex. **`https://subdomain1.domain1.com,https://subdomain2.domain2.com,http://serverB.domain3.net:8080`**

[Full article](https://support.need4viz.com/kb/faq.php?id=73)

### How to save custom configuration of the Data Analyzer for all Webi users

#### Symptom

- Create and configure a Need4Viz Data analyzer.
- In the Data Analyzer, configure the view as you need (change the objects viewed, change the display, create some alerters...)
- Save the Webi report. Ask a Webi user to open your report on his computer : the Data anlyzer is displayed with the default intial version (your customization seems to not be stored).

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3 Webi versions
- Need4Viz : all versions

#### Resolution

The customization realized in the Data Analyzer is not stored in the Webi report until you specify it. It is only sotred in the cache of your browser (that's why each time you open the report on your computer, your customization is correctly displayed but not on another browser's session).

To save the customization in the Webi report, please follow the steps :

- Once you have finished your settings in the Data Analyzer (organize the display, alerters...), open the "**Export settings**" panel :
- a popup appears, depending the version of N4V the popup may be different :
  - in previous versions of N4V -> select all the text inside and copy it :
  - in newer versions of N4V :Clic on "Copy" then open the Extended parameters to paste the value
- Close the popup and open the Extended parameters of the Data Analyzer (in Webi Design mode)
- Paste the text in the "Extended_config"/"Exported parameters" section then apply.
- Now save the Webi report. The customization is now saved with you report and all users will have the same display of the Data Analyzer as you.

[Full article](https://support.need4viz.com/kb/faq.php?id=89)

### How to add a custom style in the Data Analyzer

#### Symptom

- Add one (or more) custom syle(s) available in the Data Analyzer

#### Environment

- Windows Server / Linux
- Need4Viz : versions >= 2023.1.0

#### Resolution

To add custom style in the Data Analyzer :

1. On each Need4Viz server, open the file ***~**Need4Viz_folder_installation\*nodejs\node_modules\custom_element\ce_settings\EN(FR)\_list_style_da.json**
2. Add one (or more) entry to the list, one entry is composed with an id, a name and an empty description (**respect the exact syntax, the id mustn't start with a number**), for instance we add the "N4V Custom style" (id=n4vcustom) in the list :
3. Please be sure to update both EN and FR **_list_style_da.json** files with the same entries
4. Reastart the N4V services to apply the update
5. Create a copy of an existing style folder in the tomcat\webapps\N4VCustomElements\res\js\flexmonster\theme folder. For your information, the default theme used in the Data Analyzer is the "softdefault". For instance, we duplicate the "stripedblue" folder
6. Then rename the folder with the "id" used in the **_list_style_da.json** file :
7. Now you can update the **flexmonster.min.css** file inside the folder. In this file you can change existing CSS or create new entries. For instance, to add a specific background color on levels 1 & 2 of headers, you can add the following lines at the end of the **flexmonster.min.css**(add the "**!important**" suffixe to make sure your custom style is applied on the corresponding CSS class):
8. .fm-level-1.fm-header { background-color: #008cb2 !important; }  .fm-level-2.fm-header { background-color: #ffffff !important; color: #008cb2 !important; }
9. Now in Webi, you can choose your new Custom Style in the Data Analyzer settings :
10. The new style is correctly applied on the headers :
11. To help you to find the correct CSS class to update, you can use the Chrome Console (F12): select "Elements" tab the click on the upper left arrow button and select the element you want to update in the Data Analyzer, the corresponding CSS classes will be displayed in the "Styles" panel :

[Full article](https://support.need4viz.com/kb/faq.php?id=96)

## Drillbar

### What is the difference between "Global average" and "Distinct average" aggregation functions ?

#### Symptom

- Know the difference between "Global average" and "Distinct average" aggregation function in the Drillbar

#### Environment

- Linux/Windows Server
- Need4Viz : versions >= 2023.2.1

#### Resolution

Three different aggregation functions can be used in the Drillbar. The default calculation is the sum (each value will be sumed on each level of dimension). But you can also use an average calculation.

There are two average calculation functions available : the "Global average" and the "Distinct average".

To explain the difference between the two functions, we will take a dataset sample, based in eFashion universe, so you can easily reproduce it on your own environment :

- Build a Webi table with "State", "Lines" and "Year" dimensions and the "Quantity sold" measure
- Add a break on the "State" and a second break on the "Lines" object
- Create a Webi variable "Average distinct" =Sum([Quantity sold])/Count([Year])
- Create a Webi variable "Average global" =Sum([Quantity sold])/Count([Year];All)
- Put the "Average distinct" & "Average global" variables in the footer of the "Lines" break

The result is the following one :

....

Now if you insert a N4V Drillbar element using the same Webi objects :

The default calculation used is the sum (of "Quantity sold", by "Year", "Lines" and "State") :

Here, the sum of "Quantity sold" for California is 46.074 and correspond to the Webi calculation :

**1/ Global average**

In the "Extended parameters" / "Calculation" / "Aggregation", choose the "Global average" function :

The result will be the following :

For California, the calculation done by the engine correspond to the "Average global" Webi variable : Sum of "Quantity sold" (=46.074) divided by the total number of values of lower level dimensions - "Year" (=65) => 708.83

**2/ Distinct average**

In the "Extended parameters" / "Calculation" / "Aggregation", choose the "Distinct average" function :

The result will be the following :

For California, the calculation done by the engine correspond to the "Average distinct" Webi variable : Sum of "Quantity sold" (=46.074) divided by the total number of **distinct**values of lower level dimensions - "Year" (=6) => 7.679

[Full article](https://support.need4viz.com/kb/faq.php?id=103)

## Extended Parameters in Webi

### How to access the N4V Extended Parameters (and Export HTML/FTP/MSSP settings) in Webi

#### Symptom

- How to display the menu "Extended Parameters" in Webi

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3/BI2025 Webi versions
- Need4Viz : all versions

#### Resolution

**In SAPBI 4.2 SP3+**, the Extended Parameters of the N4V components are available here :

**In SAPBI 4.3 SP1**, the Extended Parameters of the N4V components are available here :

**In SAPBI 4.3 SP2+**, the Extended Parameters of the N4V components are available here :

**In SAPBI 4.3SP4+** you can access the Extended Parameters of the N4V components in the contextual menu of the widget. Right click inside the widget :

**In SAPBI 2025**, a shortcut to the Extended Parameters is available on the top right corner of the widget. Just click on the widget :

Starting SAPBI 4.3SP4 and N4V 2025.4+, you can access the parameters of our widget in a fully new panel (N4V Panel) :

To activate this panel your SAPBI Administrator needs to set the N4V design_app extension. Read the following article to achieve that : [https://www.need4viz.com/support/kb/faq.php?id=91](https://www.need4viz.com/support/kb/faq.php?id=91)

[Full article](https://support.need4viz.com/kb/faq.php?id=81)

### How to update settings of N4V widgets in SAPBI 4.3

#### Symptom

- Once a N4V widget is created in the report, how to display again the "Extended Parameters"

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.3+ Webi versions
- Need4Viz : all versions

#### Resolution

In SAPBI 4.3+ the Webi portal is full HTML5 technology. Due to this fact, there is different ways to display the N4V widgets, in Reading/Design mode.

**1/ Custom Element interaction in Reading mode :**

Throught this mode, you have access to the full interactivity of our widgets. You can display tooltips, drill, zoom, filter... inside the elements.

In Reading mode of Webi, the following button must be set to activate the interaction inside our widgets :

When you disable the interaction, the you have access to the default features of Webi blocks :

By default, the interaction is enabled in Reading mode.

**2/****Custom Element interaction in Design mode :**

In design mode, the interaction should be disable to give you access to the parameters of the widgets. If you cannot select a widget or display its settings, that means the intearction is enabled. Disable it to set your widget.

When Interaction is disabled :

You now have access to the Extended Parameters (right click inside the widget) :

[Full article](https://support.need4viz.com/kb/faq.php?id=124)

## Gauges

### How to use a custom picture in pictural stack or pictural gauge

#### Symptom

- Configure a Need4Viz pictural element with a custom picture

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : all versions

#### Resolution

To configure a Need4Viz pictural element with a custom picture :

1. Open a new Webi document an insert a Need4Viz pictural gauge (or stack). By default, the man pictural is displayed
2. Open your svg custom picture in Notepad (or other text editor) and find the tag "path" and the "d" property :
3. Copy the content of the d value (from m... to ...z)
4. Open the Extended parameters of the Need4Viz pictural component and go to the "Picture" tab
5. Select "Custom" in the predefined list and paste the "d" content in the "SVG Path" field
6. Validate and see the result :

#### Attachments

You can use the following values. Copy/Paste them in your Pictural component (from m... to ...z)

- to get a plane : **m430.37 48.711c29.15-29.153-11.17-67.267-39.96-38.479l-106.3 106.3-243.52-64.372-40.59 40.595 200.71 105.71-81.18 81.17-63.104-7.75-32.106 32.11 71.595 37.64 37.645 71.6 32.1-32.11-7.38-62.74 81.18-81.17 103.43 199.39 40.6-40.6-61.63-238.58 108.51-108.71z**

- to get a € : **m 224.99996,16.22698 -8.11342,36.41161 q -24.14255,-19.78892 -54.61741,-19.78892 -41.3588,0 -65.00658,23.74671 -23.647774,23.7467 -28.397115,53.23215 l 134.960355,0 -5.14505,26.71508 -132.981532,0 -0.395848,7.71771 0.395848,18.20566 127.242642,0 -5.14505,26.71508 -117.941954,0 q 7.519719,40.17154 32.552754,59.06997 25.03303,18.89844 56.49745,18.89844 37.20302,0 57.98149,-19.59107 l 0,40.9631 Q 192.34828,300 162.26913,300 53.034301,300 30.474864,189.18206 l -30.474864,0 5.738751,-26.71508 20.580475,0 q -0.395708,-4.74934 -0.395708,-17.80995 l 0,-8.11342 -25.923518,0 5.738751,-26.71508 23.152999,0 Q 39.181988,55.21112 76.583149,27.60556 113.98417,0 163.06069,0 199.868,0 224.99996,16.22698 z**

- to get a $ : **m 233.72993,14.801025 30.97001,0 0,28.342438 c 43.74979,3.151313 73.84925,20.828602 90.29846,53.031922 7.70085,14.345095 11.5514,30.970295 11.55166,49.875645 l 0,0.51269 -41.48025,0 c -0.3527,-26.94825 -10.49978,-46.3719 -30.44129,-58.271026 -7.00701,-3.84488 -14.70812,-6.4671 -23.10333,-7.866669 l -6.82525,-0.528717 0,130.721282 c 35.00194,10.85225 57.57653,19.07673 67.72384,24.67346 l 1.05744,0.52872 c 29.39427,16.80162 44.26776,43.5739 44.62051,80.31693 l 0,0.52871 c -2.7e-4,36.40144 -11.89906,65.2779 -35.69641,86.62949 l -12.6091,9.45282 c -17.14346,10.14709 -38.8422,16.27272 -65.09628,18.37692 l 0,54.07333 -30.97001,0 0,-54.07333 c -53.90784,-3.50343 -88.38657,-25.73088 -103.43627,-66.68243 -5.59695,-16.09643 -7.87203,-34.29709 -6.82526,-54.60205 l 41.48025,0 c 2.44593,25.90187 6.12024,43.05579 11.02295,51.46179 l 2.09885,3.66897 c 12.2512,16.80149 30.80434,26.77768 55.65948,29.92859 l 0,-142.80166 c -32.55624,-9.80512 -54.60746,-18.90546 -66.15371,-27.30103 -24.85508,-17.84799 -37.28259,-43.22639 -37.28256,-76.13525 l 0,-0.5127 c -3e-5,-51.098309 24.50251,-84.001566 73.50769,-98.709868 9.10023,-2.798089 19.07642,-4.896933 29.92858,-6.296539 z m 0,191.619875 0,-125.994875 C 200.12694,84.97653 180.3508,100.54963 174.40147,127.14539 l -1.57013,15.74935 c -6e-5,31.49897 20.29945,52.67433 60.89859,63.52616 z m 30.97001,50.40436 0,138.07525 c 21.35144,-2.45664 37.45326,-8.93475 48.30551,-19.43435 14.69704,-13.99226 22.04567,-31.31707 22.0459,-51.97449 l 0,-0.52872 c -2.3e-4,-21.34082 -8.22471,-37.26106 -24.67347,-47.76077 -10.15797,-6.30173 -25.38393,-12.42737 -45.67794,-18.37692 z**

[Full article](https://support.need4viz.com/kb/faq.php?id=20)

### How to add custom pictures in Need4Viz picturals components

#### Symptom

- Add custom pictures in the list of values of Pictural gauge et Pictural stack

#### Environment

- Windows Server
- Need4Viz : versions >= 12.1

#### Resolution

To add a custom picture in the list of values of available pictures in Need4Viz Pictural gauge and Pictural stack (the list is common to this 2 charts) :

1. Get the path in the svg file of your custom picture
2. Open the file **_list_picturals.json** in the folder ***~Need4Viz_folder_installation\*nodejs\node_modules\custom_element\ce_settings\lang_EN**
3. Copy an existing entry ("man" for example)
4. And past it in the existing list (between "man" entry and "custom" entry). change id by an new key (must be uniq, in lowercase, without space or special characters). Change the name by a new value (can be whatever you want)
5. Ssave the file. Do exactly the same update in the file **_list_picturals.json** in the folder ***~Need4Viz_folder_installation\*nodejs\node_modules\custom_element\ce_settings\lang_FR**
6. Open the file **list_picturals_paths.js** in the folder ***~Need4Viz_folder_installation\*nodejs\node_modules\custom_ele****ment\ce_libs\resources**
7. Create a new line with entry corresponding to the key you created in the json files and the svg path of your picture. Entrey has to be "exports.id_of_picture"
8. Save the file
9. Restart the Need4Viz server
10. The new entry is available in your Pictural components

#### Caution

The update of the Need4Viz files is not supported.

- Make a backup of each file you modify before any update
- Respect the exact syntaxe of the files (do not omit characters ";" "{" "}"...)
- Do not delete the existing values of the list (man..., custom)
- Before an upgrade of Need4Viz product, make a backup of your updated files, the upgrade will get back in it's original state the previously modified files.
- After a Need4Viz upgrade, modify the new files installed, do not replace them with previously modified in lower version of Need4Viz product

[Full article](https://support.need4viz.com/kb/faq.php?id=21)

### How to use a SVG with multi paths in a pictural stack or pictural gauge

#### Symptom

- Use a SVG picture composed by multiple paths in a Need4Viz pictural element

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : all versions

#### Resolution

By design, pictural elements don't work with SVG composed by multiple paths. Only single path can be used in pictural stack & gauge.

The workaround is to merge the paths into one and use it your pictural.

To merge the paths, you can use a tool like [Inkscape](https://inkscape.org/) and follow the steps :

1. Open your SVG file with Ctrl + O
2. Select all paths with Ctrl + A
3. Combine all paths with Ctrl + K
4. Save the new file with Ctrl + S

One it's done, open the file in a text editor such as Notepad++ , select the content of the single path and use it in your pictural stack or gauge.

[Full article](https://support.need4viz.com/kb/faq.php?id=36)

## Hyperlinks

### How to use Hyperlinks & OpenDoc syntax inside N4V components

#### Symptom

- Add an hyperlinks or an OpenDoc URL inside a N4V component

#### Environment

- Windows/linux Server
- Need4Viz : All versions

#### Resolution

To use an Hyperlink or an OpenDoc URL inside a N4V component, you must use a custom N4V function called "openlink" that will be able to render the hyperlink.

Depending on the N4V component you use, the syntax may change, you must use the strict syntax described below for each component (be careful to the quotes, double quotes...).

- Table filters

The corresponding object used for the "State" column is :

- Tiles

The corresponding object used for the "State" header is :

- Google maps

The object dimension "link/Itin" is feed by the following value (a click on a bubble open a detailed report) :

- Other charts

On other charts, to make the X axes values or the labels clickable, use the following syntaxe for your dimension object :

You can retrieve those examples in the report catalogue 7 on our demo plateform :

[Full article](https://support.need4viz.com/kb/faq.php?id=59)

## Mapline, WebMapline & Drilldown mapline

### How to add custom layers in Need4Viz Maplines

#### Symptom

- Add custom layers for a specific map used in the Mapline component

#### Environment

- Windows Server
- Need4Viz : versions >= 2021.1.0

#### Resolution

To add custom layers for a specific map used in the Mapline component of N4V :

1. Get the name of the map file used by the component, on which layers should be added. The maps are js files in the folder ***~Tomcat_folder\webapps\N4VCustomElements\res\js\highcharts\maps_xx\***(ex. ***fr-regions.js***for the French region map).
2. Create a new file with exactly the same name as get in the previous step (but with .json extension instead of .js), in the target folder ***~Need4Viz_folder_installation\*****nodejs\node_modules\custom_element\ce_lib\resources\mappoints\**(ex.***fr-regions***.**json** )
3. The structure of this new json file as to respect exactly the following :
4. Save the file
5. In the mapline component, create a chart based on the choosen map
6. In the settings / extended parameters, open the layers menu and tick the 3 first options
7. You should see the result when applying the settings
9. You can limit the layers to display on the map by setting the list (use ";" separataor) with layers name

#### Options

You can change the type of marker used on the map.

For geometric maker, you can use `'circle'`, `'square'`,`'diamond'`, `'triangle'` and `'triangle-down'`. You can also change color of the marker with the "fillColor" propertie.

For a specific online image, you can use `'url(path/graphic.png)'`, but the graphic.png file should be accessible by the server in case of print.

For a specific embeded image, you can convert your image on base64 file and use it as`'url(data:image/png;base64,iVBORw0KGgo....)'`

#### Caution

The use of custom files needs to respect exactly the instruction and structure mentionned above.

You can see an example of file in attachment.

[Full article](https://support.need4viz.com/kb/faq.php?id=23)

### Customize the list of maps in the Mapline and Drilldown mapline component

#### Symptom

- Configure the list of maps available in the Need4Viz Mapline or Drilldown mapline components

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : all versions

#### Resolution

To configure the list of maps available in the Need4Viz Mapline (to hide some maps provided by default with the solution but not used from your side), Repeat the following tasks. For example, to hide the :

1. For example, to remove the "France : Regions" from the list of maps available in the Mapline component :
2. On the Need4Viz server, go to the folder **~Need4Viz\nodejs\node_modules\custom_element_DEV\ce_settings\lang_EN** and edit the **_list_genmaps.json** file in blocnote or notepad++ editor. Make a copy of the file before any update !!
3. Delete the lines relative to the map (be careful to let the comma between the accolades) :
4. Once lines are deleted, save the file.
5. Make the same task on the file **_list_genmaps.json** in the folder **~Need4Viz\nodejs\node_modules\custom_element_DEV\ce_settings\lang_FR**
6. When saved, you can see the result directly in Webi, ther is no need to restart the service.

#### Caution

The update of the Need4Viz files is not supported.

- Make a backup of each file you modify before any update
- Respect the exact syntaxe of the files (do not omit characters "," "{" "}"...)
- Before an upgrade of Need4Viz product, make a backup of your updated files, the upgrade will get back in it's original state the previously modified files.
- After a Need4Viz upgrade, modify the new files installed, do not replace them with previously modified in lower version of Need4Viz product

[Full article](https://support.need4viz.com/kb/faq.php?id=25)

### How to generate the pies coordinates automatically in Custom Map with QGIS

#### Symptom

- Add automatically the pies coordinates for each zone of a Custom Map (used in the Mapline or Drillmap components) with QGIS

#### Environment

- QGIS v3.x
- Need4Viz : all versions

#### Resolution

To add automatically the pies coordinates for each zone of a Custom Map, you need to add the "latitude" and "longitude" attributes of the center of each zone. This could be done automatically with QGIS by a calculation of the centroïdes.

Check the projection of the map. If it's not a WGS84, reproject the map in the WGS84 coordinates :

Open the table attributes

Edit the table

Add a new field

Create the "latitude" text field (length = 0)

Choose the newly created field "latitude" :

And clic the "E" symbol to open the Expression dialog

Enter the formula **y(centroid($geometry))** (the output preview should give a correct latitude coordinate) :

Once validated ("OK"), update all the attributes :

In the same way, create a new text field "longitude" and feed the corresponding value with the formula **x(centroid($geometry))**

Save the edition and close the table attributes window

Then export the new layer :

If you want the pie of a specific zone to be displayed with different coordinates (to get a better render), just update the latitude and longitude coordinates attributes of the corresponding zone in the Geojson (or .js) file.

[Full article](https://support.need4viz.com/kb/faq.php?id=83)

### How to reproject your geojson map in QGIS to get a more "realist" view

#### Symptom

- When using a geojson map file built with WGS84 coordinates in Webi, the mao may be "stretched".
- To get a more "real" view, you need to reproject your map (through QGIS for instance) in order to use it in your mapline/drillmap components

#### Environment

- QGIS v3.x
- Need4Viz : all versions

#### Cause

N4V offline map components cannot project map themselves so a pre-projection need to be provided inside the geojson file.

#### Resolution

To reproject your map (built with WGS84 coordinates), open the file in QGIS :

Choose the "Reproject Layer" tool:

Choose a target projection (for european countries, choose for example the "Lambert 93 projection) :

Then Run and Close.

Export the Reprojected layer :

Save the features in a new json file :

Use the reprojected geojson to build your N4V map.

Enrich the properties of the map with the "hc-transform" property. The value for this property can be found in QGIS. Open the Project properties / CRS panel, then choose the projection Lambert 93. In the bottom window, you'll find the "proj4" value corresponding to your projection. This is the value you need to fill in the hc-transform property of your map :

Once the map is achieved, you should see a correct projected view in Webi :

[Full article](https://support.need4viz.com/kb/faq.php?id=87)

### How to customize the position and value of the zone label on your Mapline/Drillmap/Webmap

#### Symptom

- Change the position of the zone label on the map
- Use a different value for the zone label

#### Environment

- Windows Server / Linux
- Need4Viz : all versions

#### Resolution

Various properties can be added in the geojson file of your custom map in order to be used in the N4V Mapline/Webmap/Drillmap components.

The standard properties used in the N4V components are the following :

- "**code**": the zone code used for the mapping of your data in Webi
- "**name**": the default zone label displayed on the map
- "**latitude**" & "**longitude**": position of the Pie chart on the zone (in GPS lat/lon coordinates)
- "**hc-middle-x**" & "**hc-middle-y**": position of the zone label on the map. By default the label is placed in the middle of the zone polygon barycenter (smart calculation by the N4V engine). But if the "hc-middle-x" & "hc-middle-y" are set, they are used to place the label. Those values can be set between 0 and 1 (0.5 is the middle of the zone polygon). You can change the values to create an offset for the label display on the polygon.

You can also add other labels as you wish to display a different area name according to your needs. For example, if in some cases you want to display a short name (abbreviated, lowercase, ...) on a slightly smaller map, you can add one or more different properties:

- "**short_name**": the short/abbreviated name
- "**lowercase_name**": the name in lowercase or on several lines (use the HTML tag  to add a line break in the name of the zone)

Ex. of geojson with custom properties :

When you have added the additional zone label properties, you must declare them on the N4V engine side, in the **\Need4Viz\nodejs\node_modules\custom_element\ce_libs\resources\list_maps_codes.js** file:

After restarting the N4V services, you can then use these labels in the component (instead of the default "name" field):

[Full article](https://support.need4viz.com/kb/faq.php?id=100)

### How to reduce the weigth of the geojson mapline file

#### Symptom

- Reduce the weigth (size) of the geojson file used in the Mapline, Webmapline & Drillmap components

#### Environment

- Windows Server / Linux
- Need4Viz : all versions

#### Resolution

Each time you display a custom map in a Mapline, Webmapline & Drillmap components, the geojson file is dynamically loaded on your laptop (by the browser). If your custom geojson file is heavy (more than 2 or 3 Mo), this loading can affect the performances of the browser and reduce speed to load the report (Webi report or HTML export page).

To enhance the performance, you can generally reduce the weight of your custom map without affect the details of the rendered map.

To do that, you can use an online tool like Mapshaper (or an internal tool if you have it). Mapshaper is accessible here : [https://mapshaper.org/](https://mapshaper.org/)

Load into this tool your initial geojson file. If the file is correctly formatted, your map will be displayed on the tool. In the following example, the file size is more than 30Mo with extremly detailed borders :

To reduce the size of the file and visualize the render, you can click on "Simplify" then "Apply"

Now you can adjust the level of borders details using the slider:

In our example, if we adjust the level of details to 5%, the render is still correct :

You can now export the simplified geojson file clicking on "Export" and selecting "GeoJSON" file format:

In our example, the new generated geojson file size is now about 1Mo (compared to the 30Mo initial size).

**Additional feature in MapShaper**

If the layer is set in WGS84 coordinates, you can display it on an OpenStreetMap background, clicking on the top right layers buttons :

Result:

[Full article](https://support.need4viz.com/kb/faq.php?id=105)

### How to add a custom web tile provider in the WebMapline component

#### Symptom

- Configure the list of Web tile providers available in the Need4Viz WebMapline component

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : 2024.2.0+

#### Resolution

If you have an access to Web tile providers (Esri, Google Maps, Maptiler...) and want to use those providers on the WebMapline component, you may want to add them in the list of available web providers.

Here are the steps to achieve that:

1. On the Need4Viz server, go to the folder **~Need4Viz\nodejs\node_modules\custom_element_DEV\ce_libs\resources** and edit the **list_webproviders_conf.js** file in blocnote or notepad++ editor. Make a copy of the file before any update !!
2. Add a bloc for your provider (in this example, the ID for this entry will be CUSTOM1) as following (be aware to respect the syntax):
3. On the Need4Viz server, go to the folder **~Need4Viz\nodejs\node_modules\custom_element_DEV\ce_settings\lang_EN** and edit the **_list_webproviders.json** file in blocnote or notepad++ editor. Make a copy of the file before any update !!
4. Add a bloc for your provider (use the same ID as previously defined in the list_webproviders_conf.js file):
5. Restart the N4V services to apply the changes.

Now in Webi, you can choose your new provider in the WebMapline component :

[Full article](https://support.need4viz.com/kb/faq.php?id=107)

### How to use a custom PNG image in background of a webmapline

#### Symptom

- Add custom PNG image as a background of a specific geojson mapline
- PNG image must be sticked to the mapline when draging/zooming/unzooming
- Using of the WebMapline component

#### Environment

- Windows/Linux Server
- Need4Viz : versions >= 2022.1

#### Resolution

To add custom PNG file in background of a WebMapline, several actions need to be done on the PNG.

We'll describe those actions, using QGIS 3.40 tool.

**1. Georeference the PNG image**

Open QGIS and load the geojson mapline in it :

Open the Geo Referencer tool :

Open a new raster :

and select your PNG file :

Add few points to georeference the PNG (at least 4 points, on each corner of the image)

Clic on a point on the PNG. A new popup opens, clic on "From the map canvas"

On the geojson map, select the corresponding location :

Repeat the operation on 3 or more additional points :

Now the georeferenced image can be generated :

Provide a folder & name to save the TIF image, you can store the points (to update them later if necessary) :

Once the popup is closing, run the transformation (the success message should appears) :

You can now close the Georeferencer tool popup.

In the QGIS main frame, the new georeference TIF layer should be visible :

When you deselect the TIF layer, you can see the geojson layer, both of them should be correctly positioned :

**2. Generate the XYZ tiles from the TIF georeferenced image**

Once the PNG image is correctly georeferenced, the next step is to generate all the XYZ tiles used by the WebMapline component as a background of the geojson layer.

Open the Toolbox of QGIS :

In the search bar of the toolbox, search "XYZ" term and select "Raster tool / Generate XYZ tiles (folder)" :

In the popup, select the footprint calculated on the TIF layer, select also the zoom min (0) and max zoom (6) levels :

Select a destination folder and clic on "Execute" :

The next popup give the result of tiles generation :

3/ Configure the N4V server

Copy ol the folder of tiles on a Web server (for instance, you can use the N4V webapp N4VCustomElements, create a subfolder in maps_custom_tiles folder) :

Now, we'll create a new provider entry for the WebMapline component. Open the Need4Viz\nodejs\node_modules\custom_element\ce_libs\resources\list_webproviders_conf.js file with Notepad++ and add the following entry (replace "your_boe_server_URL" with the value of the URL & port used to access the BOE portal, please respect exactly the syntax) :

`exports.TEST = {url: "https://your_boe_server_URL/N4VCustomElements/res/js/highcharts/maps_custom_tiles/test/{z}/{x}/{y}.png"};`

Save the file.

Now we'll add the new entry in the list of providers available in Webi. Open the**Need4Viz\nodejs\node_modules\custom_element\ce_settings\lang_EN(FR)\_list_webproviders.json**and add the following entry (please respect exactly the syntax) :

Now you can restart the N4V services.

Open Webi and create a new WebMapline component using the geojson original layer and the newwly created TEST webprovider :

The result is the following one :

When you drag and zoom in the map, the background image is correctly attached to the geojson layer :

You can obtain the better result with a PNG that can be exactly positioned on top of the geojson layer (this is not exactly the case in our example, that's why the PNG doesn't fit exactly the geojson layer).

[Full article](https://support.need4viz.com/kb/faq.php?id=121)

## Multi Drill

### How to use a precalculated measure in the Multi Drill component

#### Symptom

- You want to display in the Multi Drill, a measure that must no be aggregated on each level of drill (for instance, a ratio or a distinct count)

#### Environment

- Linux/Windows Server
- Need4Viz : versions >= 2025.2

#### Resolution

When you provide a measure in the Multi Drill, an aggregation is automatically done by the N4V engine on each level (the **sum** is the default aggregation function). This works very well when you ant to display an amount or another aggregation measure.

But when you want to display a special measure like a ratio (percentage) or a distinct count, the values displayed can be wrong because the N4V engine hasn't any access to the full dataset of Webi and cannot calculate correctly the measure on each level.

We have introduced in the 2025.2 release a new specific data feed measure called "Precalculated Measure". The goal of this data feed is to provide directly to the N4V engine a measure precalculated directly in Webi for all the drill levels and only displayed as it by the component (without any additional aggregation).

For instance, in the report below, we want to display on the same drillable chart, the amount of orders (measure "Price") and the count of distinct orders (Order ID = "Num Commande") , for each categories of materials (cat level 1, 2 & 3) :

We create 3 Webi variables to calculate the count of order on each level (Count_CMD_Lev1, Count_CMD_Lev2, Count_CMD_Lev3), defined by :

Then in the Multi Drill data feed, we assign data as following ("Price" will be a standard aggregated measure, othe measures will be displayed without any aggregation) :

It is mandatory to have the same number of objects to assign the "Precalculated measure" thant there are dimension objects (for the drill levels).

[Full article](https://support.need4viz.com/kb/faq.php?id=117)

## Online maps

### How to configure the Google Geocoding component

#### Symptom

- Configure the N4V Google Geocoding component

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3 Webi versions
- Need4Viz : all version

#### Resolution

This is some information about how to create and configure the Google Geocoding component in your Webi report :

1. Open a new Webi document and add a query retrieving the objects used by the component. Generally as a result in your Webi report, you'll get at least the following objects :
  1. **Address**: the address of the point you want to show. It can be a full address (Ex. : "55 Rue du Faubourg Saint-Honoré, 75008 Paris") or a partial address ("Paris"). You need to be able to take the address and give it to google maps in Chrome (so the geocoding will work in the component)
  2. **Tooltip** : The content of the tooltip you want to display when the user will mouse over the point (it can be the Address object, another dimension object or a formula)
  3. **Measure** : the measure you want to display on the point (the radius of the circle placed on the point will correspond to the value of the measure)
2. You can now create a first Google Maps Geocoding chart and feed it with the mandatory settings :
  1. **Address**: the address of the point
  2. **Tooltip** : The content of the tooltip you want to display
  3. **Link/Itin** : This dimension is used in many ways :
    1. **Linking elements** : If you activate the lasso selection (allowing multiple selection), then this dimension will be sent to the multi value Input Control affected to the lasso selection :
    2. **Hyperlink**: if the value is formatted as an hyperlink (an URL), you can activate the hyperlinking on this value when user click on the marker on the map :
    3. **Itinerary**: if you activate the itinerary module, this dimension will be used to build the lists of values for the Start and End point.
    4. If you don't need to use one of these 3 ways, you can simply feed this dimension with the "Address" object.
  4. **Measure**: this value is used to draw the circle arround the point. It can be a dynamic value (radius of circles will vary depending on this value) or a static value (all circle will have the same size on the map).

Now you have a first Google Maps Geocoding chart. You can enrich this chart by adding some additional dimensions :

1. Create a specific color value for each point (or each family). For instance, you display all the bike rental station on your map and want to categorize them by the status of the station (closed/open/work in progress). You just have to create a variable in Webi (dimension) to affect a color code to each value of the status (ex. ***=If([status]="open") Then"#00B5CD" Else If ([status]="closed") Then "#FFBE0D"***...).
2. Assign this variable to the 4th parameter of your Google Maps chart (Color). Now each circle is colored depending on the color value of the dimension.

After that, if you want to display a legend on your map, you need to define the labels affected to each color :

1. Create a variable in Webi (dimension) to affect a label value to each value of the status (ex. ***=If([status]="open") Then "Opened station" Else If ([status]="closed") Then "Closed Station"***...).
2. Assign this variable to the 5th parameter of your Google Maps chart (Legend). Now a legend is displayed on your map with the status and affected colors for each station. You can click on the values of the legend to hide/display the correcponding points...

#### Annexe

For geocoding address, the N4V server needs to access the internet (because, for each address, it ask the correpsonding localization to Google).

To use these component, you need to configure your Google key in the configuration of N4V server.

Usage of MongoDB instance is advisable because for each address localized by Google is stored in the MongoDB database then the next time the component is refreshed with the same addresses, N4V server will previously check if the localization exists in the MongoDB database before asking to Google, so you will save Google localization credits.

The usage of the Google Maps Lat/Lon is exactly the same as the Google Maps Geocoding component excepting that the Address is replaced by 2 dimensions : Latitude and Longitude.

[Full article](https://support.need4viz.com/kb/faq.php?id=46)

### How to enable Google Maps API Key

#### Symptom

- Use a N4V Google maps component (Google Heatmap, Google Lat/Lon or Google Address map).
- A message "**For development purposes only**" may appear on the Google map

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3 Webi versions
- Need4Viz : all version

#### Resolution

Usage of Google maps is allowed only within a Google API Key you have to generate for your own company.

The steps for generation of the Key can be found here (**you can dismiss the step "Add the API key to your request"**):

[https://developers.google.com/maps/documentation/javascript/get-api-key](https://developers.google.com/maps/documentation/javascript/get-api-key?hl=)

After the steps "Create API keys" and "Restrict API keys", you can retrieve your key and follow the below steps to activate your N4V Google maps components :

1. Edit the **Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js** file
2. Set your google key in the "**GoogleKey**" parameter (put your key between quotes):
3. Save the **config.js** file
4. Open a PowerShell window and launch the command "**pm2 start all**"
5. Try your N4V Google maps component in Webi

You can get information about the pricing of Google maps usage here : [https://mapsplatform.google.com/pricing/](https://mapsplatform.google.com/pricing/)

#### Possible issues

If you get an error about the new created Google API Key, find below the Common Causes and Solutions:

- **Invalid API Key:**

- **Incorrect API Key Restrictions:**
  - **Cause:** You might have set restrictions on your API key in the Google Cloud Console, and those restrictions are preventing it from being used on your website. Restrictions commonly include:
    - **HTTP Referrers:** Your key is only allowed to be used on specific domains (e.g., `example.com`, `www.example.com`). If your website's domain doesn't match, the key will be rejected.
    - **API Restrictions:** Your key is only permitted to be used with specific APIs (e.g., Maps JavaScript API, Geocoding API). If the required API isn't enabled, the key won't work.
  - **Solution:**
    - **Review Restrictions:** Go to the Google Cloud Console (APIs & Services > Credentials), select your API key, and examine the "Key restrictions" section.
    - **Check HTTP Referrers:** If you've restricted by HTTP referrers, make sure all the necessary domains (and subdomains) are listed correctly. You might need to add `localhost` or `127.0.0.1` during development.
    - **Check API Restrictions:** Ensure that "Maps JavaScript API" is enabled as an allowed API.
    - **No Restrictions (Temporary):** As a quick test, temporarily set the "Application restrictions" to "None" and "API restrictions" to "Don't restrict key". If it works, you know the issue lies with the restrictions. *Remember to re-enable proper restrictions once you identify the correct settings.*

[Full article](https://support.need4viz.com/kb/faq.php?id=80)

## Table Filter & Scroll Table

### Filter Table (Excel in Webi) : Format does not not apply , Toolbar is not displayed

#### Symptom

- Need4Viz Filter table is not displayed as expected (When applying a format or adding a Toolbar for example):

#### 

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz Filter Table
2. Validate the chart
3. The filter table is displayed but header is empty and no formatting applied

**Cause:**

- To render correctly, most of the Need4Viz charts need a recent browser
- Same component in a supported browser:

#### Solution

- Use a supported browser as it is mentionned in the [Limitations & known issues](https://www.need4viz.com/dokuwiki/doku.php?id=limitation) : "Due to it's older technology, Internet Explorer is not supported for our charts, we recommand Chrome, Edge or Firefox to get the best renderer."

[Full article](https://support.need4viz.com/kb/faq.php?id=22)

### How to use Linking Element & Input Controls on datetime format dimension in the Table Filter

#### Symptom

- You need to display date/datetime values in the Table Filter component
- The Native Webi Linking Element or the Filtering Controls (radio buttons / checkboxes) don't work with date values

#### Environment

- Need4Viz : all versions

#### Solution

Create a query with a date/datetime dimension and mesure(s) then display the result in a Webi table and a Table Filter N4V :

Create a native Webi linking element on the Table FIlter

Then click on a line in the Table Filter : the filtering doesn't work :

#### Resolution

Create a Webi variable of type dimension and transform the date value to a corresponding text value :

The formula can be

- =FormatDate([Created on];"dd/MM/yyyy")
- =FormatDate([Created on];"MM/dd/yyyy hh:mm:ss a")
- ...

Change the assignment of your dimension in the Table Filter (replace the date/datetime dimension by the text variable) :

Then the native Webi linking is now working :

Remove the element linking

Then create an Input Control (simple value list) based on the Webi Variable :

In the Extended Parameters of the Table Filter and feed the Controls setting as follow :

Then select a line and click on the filter button to apply the selection : Selection is working

Remove the Input Control and create a multi value Input Control based on the Webi variable :

and change the settings in the Extended Parameters of the Table Filter :

Then select many lines and click on the filter button to apply the selection : Selection is working

[Full article](https://support.need4viz.com/kb/faq.php?id=48)

### Webi engine crashes when trying to display a N4V table including HTML text

#### Symptom

- Unable to transform a Webi table into a a N4V table when the table includes HTML text
- Webi service crashes

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform 4.2 (not reproductible in 4.3)
- Need4Viz : all versions

**Steps To Reproduce:**

1. Create a Web Intelligence Report with a Webi table including HTML content dimension
2. Transform the table into a N4V table
3. one of the following messages can be displayed after a long time :

**Cause:**

- This error occurs in Webi side, not in the N4V engine (the data are not sent to N4V since the Webi engine craches before)
- The problem is due to a bug in Webi. It seems to occurs when the text is too long or contains serie of special and/or HTML characters

#### Solution

There is no known solution to this problem.

The problem does not occurs in Webi 4.3

[Full article](https://support.need4viz.com/kb/faq.php?id=63)

## Tiles

### How to use a custom picture in trend or a progress tile

#### Symptom

- Configure a Need4Viz tile (trend or progress) with a custom picture

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2 Webi versions
- Need4Viz : from 2021.1.0

#### Resolution

To configure a Need4Viz trend or progress tile with a custom picture :

1. Open a new Webi document and insert a Need4Viz progress tile (or trend). By default, no picture is displayed
2. **First option** : your picture is accessible via an URL (on the web). Open the global settings, in the extended parameters / Design, and fill the Background image with the value **URL(your_url).** For example :
3. The image is now insert on your tile. Play with the settings (position, repetition, size) to make the better render of your picture.
4. **Second option** : your picture is on local. You have to put it on the Need4Viz webapp, in the folder ~N4VCustomElements\res\images
5. Once it's done, you can simply call it in the parameter, with simply the name (and the part of picture you want if it is a svg picture with multi parts). For example : ***svg_sample.svg#shape-apis-view***
6. The image is now insert on your tile. Play with the settings (position, repetition, size) to make the better render of your picture

#### Attachments

You can use the attached sample svg image to test. Rename it as **svg_sample.svg** once downloaded. Put it in your Need4Viz webapp folder (as mentionned above).

There are 2 parts in this svg, call the one or the second by :

svg_sample.svg#shape-apis-view

or

svg_sample.svg#shape-admin-view

[Full article](https://support.need4viz.com/kb/faq.php?id=24)

### How to design Trend and Progress tiles

#### Symptom

- You need to set easily the Trend Tiles and/or Progress Tiles
- You need to understand the different settings (feeding, height, padding, zones...)

#### Environment

- Need4Viz : all versions

#### Solution

**Feeding data**

First of all, here are the data assignment that could be done with the Trend and Progress Tiles :

**Parts and settings of the tiles**

You can find in the following screenshots, the different parts and the different settings (height, padding...) of the tiles components :

Footer of the Progress Tile :

Header label sizes :

Main measure sizes :

Footer sizes :

[Full article](https://support.need4viz.com/kb/faq.php?id=122)

## Timeline

### How to display data on weekly periods in the Timeline

#### Symptom

- Configure a Need4Viz Timeline to display data on weekly periods

#### Environment

- SAP BusinessObjects Business Intelligence Platform : all 4.2/4.3 Webi versions
- Need4Viz : from 2023.0.1

#### Resolution

To configure a Need4Viz Timeline to display data on weekly periods, you must follow two steps. The first one is the data preparation, the second one is the setting of the Timeline chart.

**1. Data preparation in Webi (or in an ETL)**

The N4V Timeline can only accept dates split into years, months, days... It cannot accept week numbers. So if you need to represent your data on weekley periods, you would prepare your data to fit the expected split.

If your data are stored day by day, the best way is to aggregate the data on the first day of each week (each monday for instance). This can be done through an ETL or directly in Webi by creating variables.

For istance, if you get in your query objects Input_Date (MM/DD/YYYY) and Measure, you need to create a variable in Webi to calculate the first day of the week relative to the Input Date.

The formula will be : =RelativeDate([Date Jour];1-DayNumberOfWeek([Date Jour]);DayPeriod)

Then you can create 3 additional variables to get the Year, Month number and Day number of these calculated date :

Now you can create your Timeline with the variables created before :

**2. Setting of the Timeline**

Now for the second step, edit the Timeline global settings

**X-Axis setting**

You can fix the X-Axis to fit weekly period through the "Fixed format of axis datetime". You can use

- **%W** : A numeric representation of the week of the year, starting with the first Monday as the first week Ex. : 46 (for the 46th week of the year beginning with a Monday)
- **%V** : ISO-8601:1988 week number of the given year, starting with the first week of the year with at least 4 weekdays, with Monday being the start of the week Ex. : 01 through 53 (where 53 accounts for an overlapping week)
- **%G** : four digit representation of the year going by ISO-8601:1988 standards Ex. : 2008 for the week of January 3, 2009

Now the X-axis is correctly formated :

**Tooltip setting**

You can also format the format of the tooltip. Specify the Week period format (use the same %W, %V and/or %V options) :

Now the tooltip is correctly formated :

[Full article](https://support.need4viz.com/kb/faq.php?id=70)
