# Enhance Webi capabilities – N4V FOR WEBI Knowledge Base

Troubleshooting and how-to articles from the official [Need4Viz Support Knowledge Base](https://support.need4viz.com/kb/), category 7. Each entry gives the symptom, context and resolution; the full article with screenshots is linked below it. Back to the [Knowledge Base index](knowledge-base.md).

## Webi as a Dashboard

### How to hide the "No data to retrieve" popup in Webi 4.2

#### Symptom

- You want to hide the popup "No data to retrieve" in your dashboard :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.2

#### **Resolution**

There is no setting in Webi to hide automatically this message in version 4.2 (an option exists only in Webi 4.3).

As this message is built-in the Webi engine, you cannot deactivate it manually.

A workaround to hide automatically this message is to script an auto validation of this message so, as soon as it appears in the report, it is automatically clicked and it disappears.

The workflow to realise this auto validation is the following :

1. In your report, insert a blank cell with the following content :
2. This script will click on the dialog box each **1000**milliseconds (1sec). You can change this setting but it is recommended to not set less thant 1sec.
3. Validate the formula and, in the Format Cell, change the Display setting to read content as "HTML" :
4. In the CMC, through Applications / Web Intelligence / Properties, enable the Javascript elements :

Now when you refresh your report and one query is empty, the message is automatically hidden (maximum 1 second after it is displayed).

[Full article](https://support.need4viz.com/kb/faq.php?id=71)

### How to set an auto refresh of your dashboard in Webi 4.2

#### Symptom

- You want to auto refresh your dashboard. With this feature, for instance, you can set your report in fullscreen mode (with N4V Fullscreen component) and display it on a TV in your office.

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.2
- N4V All versions

#### **Resolution**

There is no setting in Webi to automatically refresh a report in version 4.2 (an option exists only in Webi 4.3). There is a sample of Webi extension that can be activated in 4.2 (see the How to page here : [https://blogs.sap.com/2018/06/19/auto-refresh-webi-report-every-n-seconds/](https://blogs.sap.com/2018/06/19/auto-refresh-webi-report-every-n-seconds/)).

Another way is to follow the below steps.

The workflow to realise this auto validation is the following :

1. In your report, insert a blank cell with the following content :
2. This script will refresh the report each **10000**milliseconds (10sec).
3. Validate the formula and, in the Format Cell, change the Display setting to read content as "HTML" :
4. In the CMC, through Applications / Web Intelligence / Properties, enable the Javascript elements :

Now when you open your report, it will automatically refresh every 10 seconds.

#### 

#### **Now we can enhance this feature !**

#### 

By addind a N4V component, you can customize this feature to make the delay of refresh variable and set by the user.

1. Create a Webi variable called "Delay" (for instance) and set with ="0" content :
2. Insert in your report a Simple Slider with the following input parameters (this will generate a slider from 0 to 120 with a step of 10 and send the selected value in the Delay variable) :
3. Now update the script cell previously created to auto refresh the report with this content :
4. This script will trigger the auto refresh every N seconds (content of the Delay variable) only if the Delay is >= to 10 seconds. You can update the settings (min/max/step) of the N4V slider according to the script values as you which.
5. The result should be : and your report will automatically refresh every N seconds.

[Full article](https://support.need4viz.com/kb/faq.php?id=72)

### How to add HTML icons in your Webi tables & N4V components

#### Symptom

- You want to add some usefull icons in your visuals (up/down arrows, symbols...)

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.2/4.3
- N4V All versions

#### **Resolution**

The goal of this article is to add some custom icons in your Webi/N4V elements. For instance, you need to represent the trend of a measure with a up/down colored double arrow and add the capability to filter your data with those icons :

To achieve that, follow these steps :

1. Choose your HTML signs on a website and note the corresponding HTML code. Example of list here : [https://www.toptal.com/designers/htmlarrows/arrows/](https://www.toptal.com/designers/htmlarrows/arrows/). The codes we need for our example are :  and
2. Create a Webi formula that calculate your trend (with a conditional formula for instance) and the result is an HTML code representing the arrow :
3. Now if you want to color your arrow (red for down arrow and green for up arrow), transform the output of the conditional formula with an HTML syntax :
4. You can also put the icon in bold by addind the corresponding "b" tag :
5. Now you can use your variable in your favorite N4V element (ex. the table filter), then change the title of the dimension and set the filter of the corresponding dimension as "list of value" :
6. Now you can filter your data with your up/down arrow :

[Full article](https://support.need4viz.com/kb/faq.php?id=79)

### How to switch measure displayed in a chart

#### Symptom

- You want to switch the measure displayed in a chart (Ex. : changing from Quantity, to Sales revenue, to Margin)

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.2/4.3
- N4V All versions

#### **Resolution**

There are two ways to achieve your goal. The first one is using the N4V Multi Chart component and its settings. The second one is by using a combination of a Webi measure variable and a N4 navigation component.

***1/ Using the N4V Multi Chart component***

- Create your Webi table including the dimension and the measures you want to display :
- Turn your table into the N4V Multi Chart component :
- Open the Extended Parameter panel and change the following settings :

**2*/ Using a combination of the N4V Radio button and Multi Chart components***

- Create a first empty dimension Webi variable. This variable (ex. "Selected_measure) will contain the selected measure name to display :
- Create a N4V Radio Button based on the "Selected_measure" variable (actually this feeding will not be used) :
- Open the Extended Parameters panel and set the Radio Button component as followed
  - Use a Custom list of values (give the different measures you want to display) :
  - Affect the Control to a Variable (the "Selected_measure" variable, created previously) :
- Apply, the Radio button component should display the different measures as following :
- Create a new measure Webi variable (ex. "Measure_to_display") with the following formula (replace the values and measure with your own needs) :
- Create a N4V Multi Chart with the dimension and the "Measure_to_display" measure objects :
- Go to Reading mode. You can now select in the radio button the measure you want to display in the chart :

[Full article](https://support.need4viz.com/kb/faq.php?id=101)
