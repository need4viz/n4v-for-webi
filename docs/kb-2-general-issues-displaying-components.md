# General issues displaying components – N4V FOR WEBI Knowledge Base

Troubleshooting and how-to articles from the official [Need4Viz Support Knowledge Base](https://support.need4viz.com/kb/), category 2. Each entry gives the symptom, context and resolution; the full article with screenshots is linked below it. Back to the [Knowledge Base index](knowledge-base.md).

## Button Custom Elements greyed out

### Cannot "Turn Into" or "Insert Custom element" in a Webi report

#### Symptom

- The "Turn Into Custom Element" button and the "Insert Custom Element" item are greyed out :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : 4.3
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, try to insert a new Custom Element
2. or create a webi table bloc a try to turn into Custom Element this block
3. The "Turn Into Custom Element" button and the "Insert Custom Element" item are greyed out

**Cause:**

**A:**

- One or more Need4Viz service declared and active in the CMC are not started (or not works correctly).

**B:**

- The N4V services are declared with "localhost" URL in the CMC and the N4V services are not running on the Tomcat server (split deployment)

#### Solution

**A:**

Check that all the N4V services declared in the CMC are available :

- You can try to disable services one by one (untick them in the CMC and save) until the button "turn into" is available.

**B:**

In SAPBI 4.3, when they are declared with "localhost" URL, N4V services needs to run on the Tomcat server (even if the Webi process are running on another server) because the BILaunchpad (hosted on Tomcat) checks if the services are running and this request is made by the Tomcat itself (so the localhost services must answer).

- Run the N4V services on each SAPBI server (Tomcat Web Application server & BI server)

[Full article](https://support.need4viz.com/kb/faq.php?id=65)

### Custom Element button is intermittently greyed out

#### Symptom

- The "Turn Into Custom Element" button and the "Insert Custom Element" item are intermittently greyed out :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : 4.3
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, try to insert a new Custom Element
2. or create a webi table bloc a try to turn into Custom Element this block
3. The "Turn Into Custom Element" button and the "Insert Custom Element" item are intermittently greyed out

**Cause:**

The antivirus on the SAPBI server interrupt, during its scan, the communication between SAPBI/Tomcat services and N4V services.

#### Solution

An SAP note exists about exclusions rules to apply on your antivirus on a SAPBI server : [https://me.sap.com/notes/1497394/E](https://me.sap.com/notes/1497394/E)

#### **Synthesis of this SAP Note :**

#### Symptom

- When antivirus or security scanner applications are enabled, Business Objects services do not start remaining in initializing status; when antivirus is disabled the services start fine.
- What processes and directories should be excluded from anti-virus software scans and monitoring?
- Anti-virus software scans or security scanners are affecting the performance of the SAP BusinessObjects applications and on the client is leading to other errors e.g.: login failures from Web Intelligence Rich Client and Crystal Reports Client.
- Is there an antivirus or scanner exclusion list?

#### Environment

- SAP BusinessObjects Enterprise XI 3.1 (Any Service Pack)
- SAP BusinessObjects Business Intelligence 4.0 / 4.1 / 4.2 / 4.3 (Any Service Pack)
- All supported Windows Server versions
- Anti-virus:
  - McAffee VirusScan
  - Norton Antivirus (Symantec)
  - Trend Micro OfficeScan
  - Microsoft
  - Kaspersky
  - Panda
  - Cylance
  - Blackberry
  - Others

#### Reproducing the Issue

- Install & enable antivirus on BI installation server
- Start BI servers/services
- Validate servers stuck in initializing status or performance issues (check the CPU performance filtered by process)
- Disable antivirus
- Restart SIA and validate servers/services start successfully

#### Cause

Installed antivirus is blocking SAP Business Intelligence files

#### Resolution

**SAP does not support the configuration or exclusion format of Antivirus software nor performs testing with antimalware solutions with product releases, and further inquiries should be directed to the third party software vendor.**

SAP Product Support recommends the following binaries should be excluded from active scanning: %InstallDir%\ and all sub folders :

AAAnalytics.exe  AADashboard.exe  SvcMgr.exe  CMS.exe  ConnectionServer.exe  ConnectionServer.exe (32bit)  crcache.exe  crproc.exe  crproc.exe (32bit)  crystalras.exe (32bit)  EventServer.exe  fileserver.exe  JobServer.exe  JobServerChild.exe  sia.exe  WIReportServer.exe  xccache.exe  xcproc.exe  java.exe  tomcat6.exe  sqlservr.exe  svnserve.exe (32bit)  dbsrv12.exe  dbsrv16.exe  dbsrv17.exe  tomcat7.exe  tomcat8.exe  tomcat9.exe

When performing an installation, update or repair, the following executables should also be excluded (in addition to the above):

ActionAgentProc.exe Setup.exe Setupengine.exe

**Note:** After the upgrade / repair / modify is performed these rules can be removed

The following directories **and subdirectories of these**should be excluded from monitoring/scanning.

- %INSTALLDIR%\SAP BusinessObjects Enterprise XI 4.0\win32_x86
- %INSTALLDIR%\SAP BusinessObjects Enterprise XI 4.0\win64_x64
- %INSTALLDIR%\SAP BusinessObjects Enterprise XI 4.0\logging
- %INSTALLDIR%\SAP BusinessObjects Enterprise XI 4.0\java
- %INSTALLDIR%\SAP BusinessObjects Enterprise XI 4.0\data
- %INSTALLDIR%\SAP BusinessObjects Enterprise XI 4.0\FileStore
- %INSTALLDIR%\SAP BusinessObjects Enterprise XI 4.0\Auditing
- %INSTALLDIR%\sqlanywhere
- %INSTALLDIR%\tomcat\bin
- %INSTALLDIR%\tomcat\webapps
- %INSTALLDIR%\tomcat\work
- Input and output FRS if these are not in the default directories
- Webi Shared Document Cache (view properties of Web Intelligence Server for this information if it is set.)

**Note that although for performance reasons it's recommended that active scanning of these files and directories be excluded during usual hours of operation and during report schedules, it is still recommended to run a full system scan during off peak hours/maintenance hours.**

***Some components may or may not be included in your particular version of BI/BOE**

[Full article](https://support.need4viz.com/kb/faq.php?id=85)

## A puzzle or an error exception is displayed

### Chart not rendered in Webi, a puzzle image is displayed instead

#### Symptom

- Need4Viz chart is not rendered in Web Intelligence documents. Instead of it, the following puzzle image is displayed :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart
2. Validate the chart
3. The puzzle image is displayed instead of the chart

**Cause:**

- To render correctly, each Need4Viz chart needs a specific Need4Viz service to communicate.
- The Need4Viz service which should render the chart is not started (or does not work correctly).

#### Solution

Check your key validity :

- Open a web browser (I.E. Chrome) and go to the URL **http://your_boe_server_url:port_n4v/about**
- The validity of your key is displayed

If the page is not displayed in your browser

- Start the Need4Viz services
- check again the validity key

If the service doesn't start correctly

- Open the ***~Need4Viz_folder_installation*/log**
- check the **n4v_xxx_err.log** file (where xxx is the service that should render the charts)

[Full article](https://support.need4viz.com/kb/faq.php?id=7)

### Exception when adding N4V component to Webi report

#### Symptom

- Unable to add a N4V component to a Web Intelligence (Webi) report
- Error: com.businessobjects.rebean.wi.exception.CustomElementExceptions$CustomElementAvailableTypesException: An exception occurred when retrieving the feeding metadata from the CustomElement third party service. (Error: RWI 00634)
- Error in Adaptive Processing Server logs:
  - Caused by: javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: java.security.cert.CertPathBuilderException: Could not build a validated path.

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform 4.2
- Need4Viz : all versions
- Tomcat configured using https

**Steps To Reproduce:**

1. Modify or Create a Web Intelligence Report
2. Right Click on report
3. Insert Element
4. Select a N4V component
5. The following message is displayed :

**Cause:**

- This error occurs when the tomcat certificate is not trusted by the Adapative Processing Server. This can occur if the certificate is invalid or the certificate authority which authorised the certificate is not in the cacerts of the sap java JVM

#### Solution

This can be resolved by importing the certificate into the personal trust store of the JVM

[Full article](https://support.need4viz.com/kb/faq.php?id=62)

### While refreshing a web intelligence document from Chrome 110+ or Microsoft Edge 110+ the web page keeps loading indefinitely

#### Symptom

- While refreshing a web intelligence document from Google Chrome Version 110+ or Microsoft Edge Version 110+ the web page keeps loading indefinitely

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform 4.2 (not reproductible in 4.3)
- Need4Viz : all versions

**Steps To Reproduce:**

1. Logon to BI Launchpad from Chrome or Edge browser version 110+
2. Open any Web intelligence document
3. Refresh it

>>Refreshing the report never ends

**Other workflows impacted:**

- Edit as geography (by Name & Longitude Latitude)
- Reset geography
- Ranges
- Insert a shared object
- Add a comment cell in report
- Big numbers
- Add a comment to an existing cell
- Disable/enable Hana online mode
- Refresh with prompts
- Apply an input control value
- Create a new Webi variable

**Cause:**

- This issue is caused by a defect in Google Chrome Version 110+ or Microsoft Edge Version 110+ frame APIs

#### Solution

- Use fiorified UI instead of the classic one (if no document editing is necessary)
- Use WebI Rich client
- Use a non Chromium based browser (Firefox, IE11, Safari)
- Downgrade Chrome or Edge to a previous version

**Additional Information:**

- A case has been submitted at Google
- A fix for SAP BusinessObjects Business Intelligence Platform 4.2 Support Package 09 will be included in the upcoming Support Package 09 Patch 13 release

**Related SAP Note:**

- The related SAP Note is available : [3299450](https://launchpad.support.sap.com/#/notes/3299450)

[Full article](https://support.need4viz.com/kb/faq.php?id=68)

### N4V components are not displayed after a 4.3SP4 or BI2025 upgrade

#### Symptom

- After an upgrade in 4.3SP4 or BI2025, open a Webi report containing existing N4V elements (or try to insert a new N4V component in the report
- The N4V component is not displayed. Instead, you get the following image :

#### Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : 4.3SP4+ / BI2025
- Need4Viz : all versions

**Steps To Reproduce:**

1. Upgrade (or install a new server) in SAPBI 4.3SP4 / BI2025
2. Ensure N4V services are correctly started (up and running)
3. Ensure the 13 Custom Elements services are correctly set in the CMC (test of each service is successfull)
4. In a Webi report, try to insert a new Custom Element (or open a Webi report containing previously designed N4V Elements)
5. The N4V elements are not displayed correctly. An error image is displayed instead :

#### Reason

1. In SP4, the Whitelist URLs configured in the CMC is more secured thant in previous version of SAPBI.
2. All URLs services need to be separately specified (especially when using localhost)

#### Solution

1. In the CMC, open the Whitelist panel (Applications / Web Intelligence / Authorized URLs)
2. Create a new authorized URL for each of the 13 N4V services
3. Exit from Webi and reconnect to the BILaunchPad
4. Open the Webi report containing the N4V Elements, they should be correctly displayed

[Full article](https://support.need4viz.com/kb/faq.php?id=82)

## N4V widget is not correctly rendered or a blank cell is displayed

### Need4Viz charts are not displayed in Web Intelligence documents (blank cell)

#### Symptom

- Need4Viz charts are not displayed in Web Intelligence documents (blank cell)

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform 4.2 SP7 p13, 4.2 SP8 p3&5, 4.3 SP0 p1
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart
2. When validated, the chart is not displayed (the cell stay blank)

**Cause:**

- This issue is caused by a defect in the SAPBI product in
  - 4.2 SP7 patch 13
  - 4.2 SP8 patch 3 and 5
  - 4.3 SP0 patch 1

#### Solution

This issue is fixed by SAP in

- 4.2 SP7 patch 13 HotFix 1
- 4.2 SP8 patch 6
- 4.3 SP0 patch 2

[Full article](https://support.need4viz.com/kb/faq.php?id=1)

### Some Need4Viz charts are not displayed in Web Intelligence documents (incorrect display or blank cell)

#### Symptom

- Some Need4Viz charts are not displayed in Web Intelligence documents (blank cell)
- Other Need4Viz charts are displayed correctly (vertical table...)
- Other Need4Viz charts are displayed incorrectly (Filter table chart)

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart (Drillbar chart)
2. When validated, the chart is not displayed (the cell stay blank)
3. Turn the chart into Need4Viz Vertical scroll table
4. When validated, the chart is displayed correctly

**Cause:**

- **A** : This issue is caused by a problem of access to the Need4Viz web application on the webserver (Tomcat). The needed **N4VCustomElements**webapp folder has probably been set uncorrectly during the Need4Viz installation setup.
- **B** : The setting of Need4Viz web application server is not correct in the config.js file

#### Solution

**A** : Please check the Need4Viz web application is correctly deployed in your web application server.

For Tomcat (or Apache) :

- check the folder **N4VCustomElements**is in the ***~installation_BOE_Folder*****\tomcat\webapps\** folder
- if not, search the **N4VCustomElements** or the res folder in your tomcat webapps folder
- move the **N4VCustomElements**\**res**folder inside the ***~installation_BOE_Folder*****\tomcat\webapps\** folder
- Open a web browser (I.E. Chrome) and go to the URL `http(s)://**your_boe_server_url**/N4VCustomElements`
- The welcome N4VCustomElement webapp page should be displayed

**B** :

1. Edit the config.js file in

***~installation_Need4Viz_Folder***\nodejs\node_modules\custom_element\ce_libs

2. Check the following settings

**Example for a standard SSL configuration**

var **URLNodeJSServer**= 'https://your_boe_server_url[';](https://www.mytomcatserver.com%27%3B%3C/p%3E%3Cp%3Evar)

var **PORTTomcat**= 443;

**Example for a standard non-SSL configuration**

var **URLNodeJSServer**= 'http://your_boe_server_url['](https://www.mytomcatserver.com%27%3B%3C/p%3E%3Cp%3Evar);

var **PORTTomcat**= 80;

3. Then stop and restart Need4Viz services.

[Full article](https://support.need4viz.com/kb/faq.php?id=4)

### Chart not rendered in Webi, the message "To build this chart, following parameters are waited..." is displayed instead

#### Symptom

- Need4Viz chart is not rendered in Web Intelligence documents. Instead of it, a message like the following is displayed :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart (I.E. Gantt Project Management chart)
2. Select 7 dimensions and 1 measures as input
3. Validate the chart
4. The message is displayed instead of the chart

**Cause:**

- The number of requested parameters is not correct.

#### Solution

To render correctly, each Need4Viz chart needs a specific minimum of dimensions, measures [optional] and regions [optional].

Read carefully the alert message, it indicates the missing elements by a red tick (the correct number of needed elements is flagged by a green tick).

In the screenshot above, 8 dimensions are needed to render the Gantt Project Management chart. Only 7 have been set. Add the correct 8 inputs and the chart should be correctly rendered.

[Full article](https://support.need4viz.com/kb/faq.php?id=6)

### Some Need4Viz charts are not displayed in Web Intelligence documents (split deployment)

#### Symptom

- Some Need4Viz charts are not displayed in Web Intelligence documents (blank cell)
- Other Need4Viz charts are displayed correctly (vertical table...)
- Other Need4Viz charts are displayed incorrectly (Filter table chart)

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart (Drillbar chart)
2. When validated, the chart is not displayed (the cell stay blank)
3. Turn the chart into Need4Viz Vertical scroll table
4. When validated, the chart is displayed correctly

**Cause:**

- This issue is caused by a problem of misconfiguration of the product on some servers because the Web server is not correctly configured in the parameter of the need4viz server.
- The URL to configure must be the one that users are accessing from their computer

#### Solution

1.Check the deployment of Need4Viz webapp on your boe Tomcat

Ensure the URL that you fill is working from a user perspective

- Open a web browser (I.E. Chrome) and go to the URL your_boe_server_url/N4VCustomElements/res/images/green_tick.png
- The following green tick should be displayed

2.Edit the config.js file in

***~installation_BOE_Folder***\nodejs\node_modules\custom_element\ce_libs

Change the following settings

**Example for a standard SSL configuration**

var **URLNodeJSServer**= '[https://your_boe_server_url](https://your_boe_server_url<a) href="[https:="" www.mytomcatserver.com';](https://www.mytomcatserver.com)

[https:="" www.mytomcatserver.comvar">';](https://www.mytomcatserver.com)

var **PORTTomcat**= 443;

**Example for a standard non-SSL configuration**

var **URLNodeJSServer**= '['](http://your_boe_server_url<a%20href=)" class="redactor-autoparser-object">http://your_boe_server_url['](https://www.mytomcatserver.com%27%3B%3C/p%3E%3Cp%3Evar)';

var **PORTTomcat**= 80;

3. Then stop and restart Need4Viz services.

[Full article](https://support.need4viz.com/kb/faq.php?id=13)

### Charts are not renderered correctly when resizing Webi page

#### Symptom

- Need4Viz chart is not correctly displayed in Web Intelligence documents. The chart is truncated :

- Expected result :

#### 

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform : all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart
2. Validate the chart. The chart is correctly renderered.
3. Change the Webi viewer as "Page mode" (instead of "Quick Display")
4. Change the scale of the Webi report or adjust the width of the report to fit 1 page size.

**Cause:**

- If you change the scale of the page to fit a specific Width/Height or Scale, Webi change the scale of all the components on the page but doesn't manage the content of it.
- From N4V server side, no information is provided by Webi about the scale of the component in the Webi page. Only size of the component (in pixels) is sent to N4V server and this size is not changed by Webi when the scale of the report is changed.

#### 

#### Solution

This is a Webi by design behaviour.

The best way is : if you design a report with N4V components that need to be printed (the report needs to fit 1 page size width), you always have to set the Scale with following properties at the begining of your design and place the components to fit the correct width/height page size without change the Scale of the page :

[Full article](https://support.need4viz.com/kb/faq.php?id=45)
