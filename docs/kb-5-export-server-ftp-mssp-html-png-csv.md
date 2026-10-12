# Export Server, FTP & MSSP (HTML/PNG/CSV) – N4V FOR WEBI Knowledge Base

Troubleshooting and how-to articles from the official [Need4Viz Support Knowledge Base](https://support.need4viz.com/kb/), category 5. Each entry gives the symptom, context and resolution; the full article with screenshots is linked below it. Back to the [Knowledge Base index](knowledge-base.md).

## Configuration

### How to configure the FTP Export in Need4Viz solution

#### Symptom

- Configure Need4Viz services to enable FTP Export
- Configure a Need4Viz component to be exported in FTP destination
- FTP export is only possible in a PASSIVE mode

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

To configure Need4Viz services to enable FTP Export :

1. Open the file ***~Need4Viz_folder_installation*/nodejs/node_modules/custom_element/ce_libs/config.js**(make a backup copy before any update of this file)
2. Set the **export_FTP**parameter to **true**(to enable the export FTP menu in the charts settings)
3. Go to the **//FTP Config section** of this file
4. Fill the **FTPMode**parameter : FTP or SFTP
5. Fill the **FTPHost**parameter : the FTP server name
6. Fill the **FTPPort**parameter : the FTP port, by default, set to 21
7. Fill the **FTPUser**parameter : the user authorized to access the FTP destination
8. Fill the **FTPPass**parameter : the password of the user authorized to access the FTP destination
9. Fill the **FTPBaseDir**parameter : the root path set on the FTP server for the user. This parameter have to end with a '**/**'. If there is no specific root path defined, set **'/'**.
10. Save the config.js file
11. Restart the Need4Viz services

To configure a Need4Viz component to be exported in FTP destination (FTP Export is configured for Need4Viz services):

1. In a Webi report, configure a new Need4Viz chart
2. Validate the chart
3. Open the **Format Custom Element** window of the chart and go to the **Export FTP** section
4. Tick the **Automatically export the chart** (to enable the export for this chart)
5. Fill the **Path destination** : path of the folder, under the **FTPBaseDir**folder on the FTP server. If the folder does not exist, it is created. Do not start with a '/' (for example : folder1/folder2)
6. Fill the **Name of the generated target HTML file**: name of the exported html file in the destination folder (for example : myfile.html)
7. Validate the settings
8. Check in the FTP folder, the file is created

#### Possible issue

In case of file not created in the destination folder, check :

1. FTP server is set as Passive mode
2. The Need4Viz server can access to the FTP server (on the port specified)
3. The **FTPUser**/**FTPPass**are set correctly and the user has the right to create a folder/file in the **FTPBaseDir**folder on the FTP server.
4. If Need4Viz is installed in a root folder containing a space character (ex. "Program files"), you need to create a specific working directory without space or special char (Ex. **C:/Need4Viz/data/ce_works**) then in the config.js file, replace the line **var WorkingPath = LocalCEPath+'/'+WorkingFolder+'/';** with **var WorkingPath ='C:/Need4viz/data/'+WorkingFolder+'/';**and restart N4V services (**"pm2 start all"** in a PowerShell window).
5. In the config.js file of N4V, check the LocalCEPath contains uniquely **'/'** directory separator (and no **'\\'**) because WorkingPath variable mustn't mix **'/'** and **'\\'** characters.

To get more informations about the issue :

1. Enable Debug mode in Need4Viz config.js file (set **LogDebug**parameter to **true**)
2. Restart Need4Viz services
3. Test again an FTP Export of your chart
4. Open the***~Need4Viz_folder_installation*/log**
5. check the **n4v_xxx_out.log**and **n4v_xxx_err.log** file (where xxx is the service that should render the charts)

[Full article](https://support.need4viz.com/kb/faq.php?id=9)

### How to configure the Export Server in Need4Viz solution

#### Symptom

- Configure Need4Viz services to enable HTML Export
- Configure a Need4Viz component to be exported in destination folder

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

To configure Need4Viz services to enable HTML Export :

1. Open the file ***~Need4Viz_folder_installation*/nodejs/node_modules/custom_element/ce_libs/config.js**(make a backup copy before any update of this file)
2. Set the **export_HTML**parameter to **true**(to enable the export HTML menu in the charts settings)
3. Restart the Need4Viz services

To configure a Need4Viz component to be exported as HTML in folder destination (HTML Export is configured for Need4Viz services):

1. In a Webi report, configure a new Need4Viz chart
2. Validate the chart
3. Open the **Format Custom Element** window of the chart and go to the **Export HTML** section
4. Tick the **Automatically export the chart** (to enable the export for this chart)
5. Fill the **Path destination** : path of the destination folder. If the folder is set localy (For example C:/temp) it refers to the folder on the Need4Viz server (not on the user's computer). If the folder does not exist, it is created. The folder can be a shared or NAS folder (for example \\my_server\my_folder)
6. Fill the **Name of the generated target HTML file**: name of the exported html file in the destination folder (for example : myfile.html)
7. Validate the settings
8. Check in the destination folder, the file is created

#### Possible issue

In case of file not created in the destination folder, check :

1. The destination folder does not need an authentification (this is not supported)
2. If the destination folder does not exist, try to export in an existing folder.

To get more informations about the issue :

1. Enable Debug mode in Need4Viz config.js file (set **LogDebug**parameter to **true**)
2. Restart Need4Viz services
3. Test again an HTML Export of your chart
4. Open the***~Need4Viz_folder_installation*/log**
5. check the **n4v_xxx_out.log**and **n4v_xxx_err.log** file (where xxx is the service that should render the charts)

[Full article](https://support.need4viz.com/kb/faq.php?id=10)

### How to configure an external WebApp for export FTP/HTML

#### Symptom

- Configure an external Need4Viz Web Application to be used by exported HTML/FTP charts

#### Environment

- Windows Server
- Need4Viz : since 2021.3.1

#### Resolution

To configure Need4Viz to use an external webapp for exported charts (in HTML files generated by FTP/HTML export) :

1. Copy the entire N4VCustomElements webapp folder (***~BOE_folder*/tomcat/webapps**) in the external web server that will be used by exported charts (Apache server for instance **~Apache/htdocs**)
2. Get the URL for this new web server (ex.: **http://my_external_server**) and check in a browser that you can access the Need4Viz webapp in this web server by entering the URL **http://my_external_server/N4VCustomElements/res/images/green_tick.png**
3. The following image should appear :
4. On the Need4Viz server, open the file ***~Need4Viz_folder_installation*/nodejs/node_modules/custom_element/ce_libs/config.js**(make a backup copy before any update of this file)
5. Set the **use_external_webapp_FTP**parameter to **true**(to enable the usage of external webapp for FTP exports), or the **use_external_webapp_HTML**parameter to **true**(to enable the usage of external webapp for HTML exports)
6. Go to the **//FTP Config section** of this file
7. Fill the **URL_PORT_WebApp_ext_FTP**parameter (for FTP export) or the **URL_PORT_WebApp_ext_HTML**parameter (for HTML export) : the URL of the external web server (without ending '/'), for instance : '**http://my_external_server**'. If a specific port need to be used, set it in the URL for instance : '**http://my_external_server:my_port**'
8. Save the config.js file
9. Restart the Need4Viz services

Test an export (FTP or HTML) of a Need4Viz component and open it in a notepad++ editor. You should see the static includes in the file are set with your external web server.

####

[Full article](https://support.need4viz.com/kb/faq.php?id=29)

### How to embed N4V HTML Export in Teams

**Important** Currently using the mobile version, you won't be able to see the n4v apps but in some case it can be see but won't work, this is a integration problem on Microsoft part currently about the custom application  **Installation**  First option:

You can go in a team or a conversation and next to the name you have a small + button, click and add "website", provide the URL of the dashboard.  Second option (available in N4V 2025.2+): Download the zip provided by N4V admin panel and download the N4V-teams-dashboard zip file, then go in the Applications, Manage your application, load an application.

If you are an administrator in Teams you simply need to choose "Upload a custom app" and choose the zip provided by the N4V admin panel

on the contrary, if you are not an administrator in Teams you can click on "Submit an app to your org" and choose the zip provided by the N4V admin panel, your administrator will need to do those steps :  go on the website : [https://admin.teams.microsoft.com/policies/manage-apps](https://admin.teams.microsoft.com/policies/manage-apps) then search the app, click on it and approve it

And everything is done, now you only need to in Teams and click on Applications, search "n4v-teams-dashboard" or the name you provided and everything is finished and ready to use.  **Update** To update the app if needed, you simply need to contact your Teams administrator to go on the same page as the installation, select the application and choose "Upload file" under New version

In Teams :

Add the new application :

Then you can Open the application :

[Full article](https://support.need4viz.com/kb/faq.php?id=113)

## Usage

### Export HTML/FTP doesn't work when scheduling Webi report

#### Symptom

- Need4Viz charts are not exported in HTML/FTP when scheduling a Web Intelligence document
- Export is working when viewing/refreshing Webi report in the BI portal

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart
2. When validated, configure the chart to export it as HTML (previous HTML/FTP configuration has already been done and works well)
3. The chart is correctly exported
4. Save and close the Webi report
5. Delete the HTML file exported (on local or ftp server)
6. Schedule the Webi report (Destination enterprise and Webi format)
7. The chart is not exported (on local or FTP server)

**Cause:**

- To enable the export function, the chart has to be rendered but in Webi format scheduling, this render is not calculated during the schedule (only during the opening of the instance in the portal).

#### Solution

To schedule an export HTML/FTP of a Need4Viz chart :

- Schedule the Webi Report as a PDF or Excel format (but it can take a long time depending on the number of charts to export)
- **or**
- Create a publication based on the Webi report and schedule this publication using mHTML format (this is the best way to achieve a scheduled export of Need4Viz components in HTML)

[Full article](https://support.need4viz.com/kb/faq.php?id=3)

### Automate the Need4Viz HTML export / Use N4V Variables to generate dynamics path and filename

#### Symptom

- Use Need4Viz Variables (like SAPBI Placeholders) to generate dynamic Folder Path and filenames
- Create a Publication in order to generate all the HTML files

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

To configure Need4Viz services to enable HTML Export :

To configure a Need4Viz component to be exported as HTML in folder destination (HTML Export OR FTP is configured for Need4Viz services):

1. In a Webi report, configure a new Need4Viz chart
2. Validate the chart
3. Add Webi Sections in order to generate as much HTML exports as you have of possible combinations (ie: if you have a dataset with 5 "year" and 3 "country"; you must generate 3*5 => 15 HTML exports). Here we created two sections, the first (1) on object [v_Year] and the second (2) on object [state_po]

1. Open the **Format Custom Element** window of the chart and go to the **Export HTML OR Export FTP (1)**section depending on what type of destination you chose
2. Tick the **Automatically export the chart (2)** (to enable the export for this chart)
3. Fill the **Path destination (3)** : path of the destination folder. If the folder is set locally (For example C:/temp) it refers to the folder on the Need4Viz server (not on the user computer). If the folder does not exist, it is created (**in lower case**). The folder can be a shared or NAS folder (for example \\my_server\my_folder\**%DR%EN%MMMMYYYY%** that will write into the folder \\my_server\my_folder\november2020\).
4. You can find the information about the available variables [here](https://www.need4viz.com/dokuwiki/doku.php?id=format_title)
5. Fill the **Name of the generated target HTML file (4)**: name of the exported HTML file in the destination folder (for example : %SECTION%1%_%SECTION%2%.html) . If value of %SECTION%1% is 2016 and value of %SECTION%2% is AL , the HTML file will be 2016_al.html

1. Validate the settings
2. Check in the destination folder, the file is created. if you browse the report, it will generate one HTML file per chart. If you browse the whole document, it will create all the HTML exports.

#### Automate the export with a publication

1. Create a new SAP BI **publication**(We don't want to use the publication to burst the report BUT only for the MHTML export format)
2. In "**Source document**", add the webi report that you just set for the Need4Viz HTML export
3. In "**Enterprise Recipient"**, select any user
4. In "**Format"**:
  1. In "Output Format", select **mHTML**
  2. In "Output Format Details", select the report on which you set the Need4Viz HTML export
5. "Prompts" (Optionally), fill the prompts
6. Click OK
7. The new publication appears in the list
8. Right click on it and select Schedule
9. Select "Run Now", wait that scheduling is in success and check that the files are generated in the folder you set in the Need4Viz component (\\my_server\my_folder\november2020 in this example)

#### Normalization of filename and path

The following formulas are applied to normalize the filename and path of the exported HTML file.

FileNameHTML.normalize("NFD").replace(/[\u0300-\u036f]/g, "");

FileNameHTML.replace(/[^a-z0-9_\-\.]/gi, '_').toLowerCase();

#### Possible issue

In case of file not created in the destination folder, check :

1. The destination folder does not need an authentication (this is not supported)
2. If the destination folder does not exist, try to export in an existing folder.
3. Numeric sections are not supported for now- please use a variable to transform the numeric value to text value

To get more informations about the issue :

1. Enable Debug mode in Need4Viz config.js file (set **LogDebug**parameter to **true**)
2. Restart Need4Viz services
3. Test again an HTML Export of your chart
4. Open the***~Need4Viz_folder_installation*/log**
5. check the **n4v_xxx_out.log**and **n4v_xxx_err.log** file (where xxx is the service that should render the charts)

[Full article](https://support.need4viz.com/kb/faq.php?id=19)

### How to export in HTML a full Webi report including N4V components

#### Symptom

- When exporting in HTML a full Webi report including N4V component, the N4V elements are generating images instead of dynamic html render

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart
2. Export the Webi report into HTML (through save as HTML or through a schedule)
3. Open the HTML archive generated (report.html).
4. The N4V components are displayed as images (PNG) and not as HTML render

**Cause:**

- Webi doesn't allow generation of HTML render for custom elements during a HTML export. It exclusively ask to the N4V engine a PNG render (as for the native Webi charts).

#### Solution

It is not currently possible to export a full Webi report as well as all the N4V components of this report in HTML at once.  Indeed, when an HTML export of the Webi report is generated, the N4V components (like the Webi charts) are exported in the form of static images.

There is a workaround to get a full HTML render of the whole report. It is necessary to go through several steps which consist of:

- export Webi full report to HTML once
- export individually (via the HTML export option in the extended parameters) the N4V components in HTML by a publication. The exported HTML files will be saved in the /images folder of the Webi HTML archive
- in the report.html replace the img tags (calling charts PNG) by iframe tags (calling exported HTML charts files in /images folder)
- in case the navigation is used between N4V elements in the Webi report, write navigation functions used in N4V components (function calls are generated within N4V components during HTML export) in the parent page of the report to update the iframes containing the graphs
- The Webi report exported in HTML therefore serves as a "shell" containing the formatting and instead of displaying the static PNG images of the graphs in the iframes, we just add the javascript function(s) to dynamically update the source of these iframes from HTML exports of N4V components.  An example of full report exported from Webi is available on our demo site: [https://demo-public.need4viz.com/N4VDemo/Sales/report.html](https://demo-public.need4viz.com/N4VDemo/Sales/report.html)  Looking at the code of this html file from an export of the Webi report, you will see the javascript functions click_link_multi and click_link_N4V_Grade which update the iframe sources according to the value selected in the navigation components.

[Full article](https://support.need4viz.com/kb/faq.php?id=61)

### Exported N4V html files cannot be displayed in Sharepoint

#### Symptom

- Need4Viz charts are correctly exported in HTML format in Microsoft Sharepoint library (**WARNING**: in online Sharepoint, the extension of N4V HTML file exported must be **.aspx**)
- The exported file connot be embedded in an Iframe in a Sharepoint page

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart
2. When validated, configure the chart to export it in a Sharepoint librabry as HTML (previous MSSP configuration has already been done and works well). **WARNING**: in online Sharepoint, the extension of N4V HTML file exported must be **.aspx**
3. The chart is correctly exported
4. Save and close the Webi report
5. Create a new page in the Sharepoint site and include an IFrame
6. Source the iframe with the previously N4V html file exported
7. An error is displayed (file cannot be found)

**Cause:**

- Custom scripts need to be activated on the site to enable the display of N4V file in an Iframe.

#### Solution

Open the admin console of your Sharepoint ([https://your_sharepoint-admin.sharepoint.com](https://your_sharepoint-admin.sharepoint.com)) logged as site administrator.

Select the "Active sites"

Select the site where are exported the N4V elements and click on "Update" the Custom Scripts :

Select "Allow" :

Now you need to re-export the N4V components (previously exported HTML file will not be viewable).

New exported file are now correctly displayed in embedded Iframe (through "incorporation" object) :

Additional information: [https://learn.microsoft.com/en-us/sharepoint/allow-or-prevent-custom-script](https://learn.microsoft.com/en-us/sharepoint/allow-or-prevent-custom-script)

[Full article](https://support.need4viz.com/kb/faq.php?id=104)

## Use N4V elements in Microsoft Office

### How to add N4V HTML widgets in PowerPoint

#### Symptom

- You want to add N4V HTML widgets into your PowerPoint Presentation

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : all versions

#### **Resolution**

**1 - Open MS PowerPoint**

**2 - Check that Web Viewer Add-In is available (in the Insert menu / My Add-Ins / Web Viewer)**

- **If it is not in the list, add Web Viewer Add-In**

**3 - The Add-In is available, you can now add your HTML export into PowerPoint**

**a - Click Insert / My Add-Ins**

Select Web Viewer

**b - Fill a HTTPS URL**

**Example :**

**c - Click Preview**

**d - The HTML is inserted into PowerPoint**

#### Possible issue

The HTML is not displayed. It works fine in a HTML browser but not in PowerPoint

- The corner radius option is not yet compatible with Powerpoint integration; please remove this option before to export the N4V widget (set it to 0)

- The URL MUST be in **HTTPS**

[Full article](https://support.need4viz.com/kb/faq.php?id=57)

### How to use and update dynamically N4V PNG elements in Word, Excel, PowerPoint...

#### Symptom

- You want to add N4V PNG widgets into your Word, Excel or PowerPoint Presentation
- N4V elements will be periodically exported from Webi (scheduling/publication) on a server
- The Office document will be updated automatically on each open

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : 2024.2.0+

#### **Resolution**

**1-**Create in Webi your N4V element and configure the automatic export on PNG format (for an easier use, create a folder link to a dedicated Tomcat webapp and use this link as target folder for the PNG export)

**2-** Check the image is correctly exported

**3-**Open MS Word and create a new document and click on "Insert / images / This device..."

**4-** Insert the file (in the image name, put the full link to the PNG file then clic on "Link to the file") :

**5-** Save the Word document and close it

**6-** In Webi, change the Palette color of your element :

**7-** Open you Word document and check the image is correctly updated :

[Full article](https://support.need4viz.com/kb/faq.php?id=95)

### How to refresh on demand all the N4V PNG files inserted as links in a PowerPoint presentation

#### Symptom

- You want to refresh all the PNG files (exported by N4V for Webi) linked inside your PowerPoint Presentation

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all versions
- Need4Viz : all versions

#### **Resolution**

**1-** Open MS PowerPoint

**2-** Press Alt+F11 to open the Visual Basic for Application (VBA) Editor

**3-** Inside the VBA Editor, select **Insert > Module**

**4-** Copy the following code in the Editor

Sub RefreshAllLinks()  Dim slide As slide  Dim shape As shape  Dim linkFound As Boolean

linkFound = False

' Loop through all slides

For Each slide In ActivePresentation.Slides  ' Loop through all shapes on the slide  For Each shape In slide.Shapes  ' Check if the shape has a valid LinkFormat (indicating it is linked)  If Not shape.LinkFormat Is Nothing Then  On Error Resume Next  shape.LinkFormat.Update  If Err.Number = 0 Then  linkFound = True  End If  On Error GoTo 0  End If  Next shape  Next slide

If linkFound The

MsgBox "All linked files refreshed successfully!", vbInformation, "Success"  Else  MsgBox "No linked files found to refresh.", vbExclamation, "No Links Found"  End If  End Sub

**5-** Close the VBA Editor and goback to PowerPoint

**6-** Press **Alt+F8**, then select "**RefreshAllLinks**" and click on **Execute**

**What does the macro do ?**

**1-****Refresh Links:** It goes through all slides and updates all linked objects (images) to reflect the current state of their source files.

**2- No Path Changes:** It does not change or update file paths, but only refreshes the content.

**3- User Feedback:** It informs you if any linked files (images) were found and updated.

**Annexe 1 : Create an icon in the Toolbar to control the macro**

**1-** Open File > Options

**2-** In the left menu, select Quick Access Toolbar

**3-** In the list "Select commands in", select "Macro"

**4-** Select your macro ("Module1.**RefreshAllLinks**") and click on "Add" to add it on the Quick Access Toolbar

**5-** To change the icon, select the Macro in the right list and click on "Update" then select a new icon or enter a new name. Click OK to validate.

[Full article](https://support.need4viz.com/kb/faq.php?id=106)
