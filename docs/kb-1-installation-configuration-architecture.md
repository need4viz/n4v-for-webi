# Installation - Configuration - Architecture – N4V FOR WEBI Knowledge Base

Troubleshooting and how-to articles from the official [Need4Viz Support Knowledge Base](https://support.need4viz.com/kb/), category 1. Each entry gives the symptom, context and resolution; the full article with screenshots is linked below it. Back to the [Knowledge Base index](knowledge-base.md).

## N4V Installation

### Error "Select action" displayed during Need4Viz patch/hotfix installation

#### Symptom

- During the installation of a Need4Viz patch or hotfix (over a previous Need4Viz installation), the following Windows message (or similar) is displayed :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all version
- Need4Viz : all versions - Full version already installed

**Steps To Reproduce:**

1. Install a full version of Need4Viz on a Windows server
2. configure and start the Need4Viz services
3. Install a patch or a hotfix of Need4Viz on the same server
4. The error message is displayed

**Cause:**

- Some files are already in use by the Need4Viz services during the installation of the patch / hotfix. Windows cannot delete them to replace them by the newer version.

#### Solution

Before installation of Need4Viz Patch or Hotfix, the Need4Viz services have to be stopped on the server.

[Full article](https://support.need4viz.com/kb/faq.php?id=5)

### Defect versions of SAPBI Product

#### Symptom

- Need4Viz charts are not displayed in Web Intelligence documents (blank cell)
- Need4Viz services cannot be registered in the CMC

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform 4.2 SP7 -> SP9, 4.3 SP0
- Need4Viz : all versions

**Steps To Reproduce:**

1. In a Webi report, configure a new Need4Viz chart
2. When validated, the chart is not displayed (the cell stay blank)

or

1. In the CMC, try to create the N4V Services but an error occured and the service cannot be created

**Cause:**

- This issue is caused by a defect in the SAPBI product in
  - 4.2 SP7 patch 13
  - 4.2 SP8 patch 3,5
  - 4.2 SP8 patch 10, 11, 12
  - 4.2 SP9 patch 4
  - 4.3 SP0 patch 1

- We are closely working with SAP team, do not hesitate to contact us if you have any issue with our components on a SAPBI version, we'll ask SAP team to fix it quickly as possible
- Sap Note : [https://launchpad.support.sap.com/#/notes/3103998](https://launchpad.support.sap.com/#/notes/3103998)

#### Solution

This issue is fixed by SAP in

- 4.2 SP7 patch 13 HotFix 1
- 4.2 SP8 patch 6
- 4.2 SP8 patch 12 Hot Fix 1
- 4.2 SP9 patch 5
- 4.3 SP0 patch 2

[Full article](https://support.need4viz.com/kb/faq.php?id=35)

### How to uninstall the product

#### Symptom

- It's unecessary to uninstall N4V for Webi. You should be able to repair it by installing the last patch or making an adjustement in the configuration file.
- In exceptional case, if you need to uninstall the product, you can simply open the Windows Unistall Program page and click on "uninstall" N4V for Webi
- If the product did not uninstall correctly, follow the below steps to finish uninstallation.

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

1. Open a PowerShell command window as local administror of the server. Run a "pm2 kill" command.
2. Open the Central Configuration Manager and stop the BOEXI40Need4Viz service :
3. Open a Prompt Command and run the command **sc delete boexi40need4viz.exe** :
4. Check in the Central Configuration Manager that the Need4Viz service does not exist anymore :
5. Delete the folder where N4V is installed : ***~Need4Viz***
6. Delete the folder where the webapp N4VCustomElements is insalled (**tomcat/webapp/N4VCustomElements**)
7. Open the Windows Services and check if MongoDB is running.
8. If necessary, Stop the MongoDBServer.
9. Open the Windows Unistall Program page and click on "uninstall" MongoDB
10. Open the Windows Registry Editor and delete the node HKEY_LOCAL_MACHINE/SOFTWARE/Need4Viz

The product is now completly uninstall from the server.

[Full article](https://support.need4viz.com/kb/faq.php?id=49)

### Full installation or patch setup does not run on Windows

#### Symptom

- During the installation of a Need4Viz patch or hotfix, nothing seems happend. In the Windows Event log the following Windows message (or similar) is displayed : Activation of app Microsoft.Windows.Apprep.ChxApp_cw5n1h2txyewy!App failed with error: This app can't be activated by the Built-in Administrator. See the Microsoft-Windows-TWinUI/Operational log for additional information.

#### Reason and Prerequisites

**Environment:**

- Need4Viz : all versions - Windows

**Steps To Reproduce:**

1. Run a setup of Need4Viz on a Windows server
2. Nothing happend
3. Open the Windows Event Log
4. The error message is displayed : Activation of app Microsoft.Windows.Apprep.ChxApp_cw5n1h2txyewy!App failed with error: This app can't be activated by the Built-in Administrator. See the Microsoft-Windows-TWinUI/Operational log for additional information.

**Cause:**

- the local security policy for Admin Approval Mode for the Built-in Administrator Account is not enabled on the Windows server.

#### Solution

You have two solutions to enable the Admin Approval Mode for the Built-in Administrator Account.

***Solution 1***

1. Press *Windows + R* keys.
2. In the run dialogue box, enter *gpedit.msc* and click *OK*.
3. Navigate to *Windows Settings > Security Settings > Local Policy > Security Options*.
4. Locate and open the *User Account Control: Admin Approval Mode for the Built-in Administrator Account*.
5. Under *Local Security Setting* tab select *Enable*.
6. Click on *Apply* and *OK* to save your changes.

***Solution 2***

Create a local user with admin rights and try again to run the setup.

[Full article](https://support.need4viz.com/kb/faq.php?id=53)

### How to update Freemium version to Full version of N4V for Webi

#### Symptom

- A Freemium version is already installed on your SAPBI (or on a standalone) server
- You want to update your installation to a full N4V for Webi version

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

As the Freemium version is a dedicated version of N4V, the best way to update is to uninstall the Freemium and install a clean Full version of N4V.

- **Uninstall Freemium**

1. Open the Central Configuration Manager and stop the BOEXI40Need4Viz service :
2. Open a Prompt Command and run the command **sc delete boexi40need4viz.exe**
3. Check in the Central Configuration Manager that the Need4Viz service does not exist anymore :
4. Open a PowerShell command window as local administrator of the server. Run a "**pm2 kill**" command.
5. Delete the folder where N4V is installed : ***~Need4Viz***
6. Delete the folder where the webapp N4VCustomElements is insalled (**tomcat/webapp/N4VCustomElements**)

- **Install Full version**

1. Download the Full setup of the latest N4V 4 Webi version
2. Launch the setup to install it on your server (follow the installation guide steps)

- **Post install**

In the CMC, keep the existing names of the 7 N4V services already created for the Freemium (change the port number according to the Readme.txt file available after installation).

Complete creation of the 6 new N4V services.

Open a Webi report including components created with the Freemium version, the components should be displayed correctly.

[Full article](https://support.need4viz.com/kb/faq.php?id=60)

### SAPBI 4.3 behind a HTTPS Reverse Proxy does not show N4V components

#### Symptom

- After the installation of N4V on a SAPBI 4.3 deployment, the N4V components are available in the Webi list of charts but inserting a chart on the report doesn't works (blank frame or error displayed)

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform 4.3
- HTTPS Reverse Proxy used to access the BI plateform
- Need4Viz : all versions

**Steps To Reproduce:**

1. Install a full version of Need4Viz on a server
2. configure and start the Need4Viz services
3. SAPBI 4.3 is used and configured behind a Reverse Proxy
4. Insert a N4V component on a Webi report
5. The following error message is displayed in the console of the browser

**Cause:**

- The main page is based on HTTPS request but the RESTful Webi API are called through HTTP request. This mixed content is prohibited by the browser and the N4V content is not displayed.

#### Solution

A configuration in the Tomcat needs to be done to declare the reverse proxy settings in the connector.

Open the server.xml file placed in the /tomcat/config directory (on the SAPBI server).

Add the following settings in the Connector tag (where the Tomcat port is defined) :

- proxyName="your_proxy_url"
- proxyPort="your_proxy_port"
- scheme="https"

For instance, if the URL to access the BI Launchpad is [https://test-sapbi.xxx.com/BOE/BI](https://test-sapbi.xxx.com/BOE/BI)

Then the Tomcat connector tag should be configured as :

Once it is done :

- Stop the Tomcat
- Clear the Tomcat cache directory (delete the **tomcat\work\Catalina\localhost\BOE** folder)
- Start the Tomcat
- Clean your BILaunchpad session
- Test a Webi report with a N4V component

[Full article](https://support.need4viz.com/kb/faq.php?id=66)

### Error "Access violation at address..." during N4V upgrade

#### Symptom

- During the installation of a Need4Viz patch (over a previous Need4Viz installation), the following Windows message (or similar) is displayed :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all version
- Need4Viz : 2024.2.0+ - Full version already installed

**Steps To Reproduce:**

1. Install a full version of Need4Viz on a Windows server
2. configure and start the Need4Viz services
3. Install a patch or a hotfix of Need4Viz on the same server
4. The error message is displayed

**Cause:**

- Since 2024.2.0 version, the upgrade setup automatically clean the working folder (Need4Viz\nodejs\node_modules\custom_element\**ce_works**) of N4V before installing the new version files. Depending of the usage of this workdir (the folder can be really huge if you make regularly an important number of N4V HTML exports), this cleaning operation can take too much time an the installer may generate the mentionned error.

#### Solution

When this behavior happend, stop the installer (click "OK" button and quit the installer) and realize all the following steps (in the mentioned order) :

1. Rename the folder Need4Viz\nodejs\node_modules\custom_element\**ce_works**to Need4Viz\nodejs\node_modules\custom_element\**ce_works_old**
2. Create a new folder Need4Viz\nodejs\node_modules\custom_element\**ce_works**
3. Open a CMD window and
  1. Goto the Need4Viz\nodejs\node_modules\**custom_element**folder
  2. Run the command "**rmdir ce_works_old /S /Q**"
  3. this step can take quite a long time. You can goto step 4 during this time (do not close the CMD window to let the step finish)
4. Run the N4V upgrade setup

[Full article](https://support.need4viz.com/kb/faq.php?id=92)

### How to enforce a full re-installation of N4V

#### Symptom

A previous full installation has failed or was incomplete and when you launch again the setup to install N4V you cannot choose to install completely from scratch but only update is done.

#### Reason and Prerequisite

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all version
- Need4Viz : 2025.1+

**Steps To Reproduce:**

Start the setup.exe

#### Solution

To be able to force the setup to launch an installation, we'll “uninstall” N4V, just do these steps:  1. press the Windows key and search for regedit or press Win + R and type regedit.exe, then launch it 2. search for Need4Viz in the left-hand tree at this location: HKEY_LOCAL_MACHINE/SOFTWARE/Need4Viz 3. Right-click on the Nee4Viz node, then click on Delete. 4. Relaunch the installation setup

[Full article](https://support.need4viz.com/kb/faq.php?id=114)

### How to run multiple instances of N4V on the same server

#### Symptom

You want to run multiple instances of N4V engines on the same server.

#### Prerequisite

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all version
- Need4Viz : all versions

#### Solution

The N4V installer cannot be used to install multiple instances of N4V.

By default, the insatller will detect the first instance already installed on the server and will update it to the latest version.

If you want to run multiple instances of N4V on the same server, you need to configure it manually.

Follow the below steps to run multiple N4V instances :

1/ Duplicate the tomcat/webapps/N4VCustomElements folder (for instance, name it **N4VCustomElementsProd**)

2/ Create a new log folder (ex. Need4Viz/logsProd)

3/ Duplicate the Need4Viz/nodejs/node_modules/custom_element folder ((for instance, name it **custom_elementProd**)

4/ Open the config.js file in the Need4Viz/nodejs/node_modules/custom_elementProd/ce_libs folder and update the following parameters :

- LocalCEPath => '/Need4Viz/nodejs/node_modules/custom_element**Prod**'
- LogUsageFile => '/Need4Viz/logs**Prod**/Chart_usage.csv'
- LogFTPUsageFile => '/Need4Viz/logs**Prod**/FTP_usage.csv'
- PORTNode_Maps => give another rang of ports (ex. 8301)
- URLmongoDB => use a new Mongo instance, ex. 'mongodb://localhost/Need4Viz**Prod**'
- Update the FullURLJSServer with the new webapp name (ex. URLNodeJSServer+':'+PORTTomcat+'/**N4VCustomElementsProd**/res/js')
- Update the FullURLIMGServer with the new webapp name (ex. URLNodeJSServer+':'+PORTTomcat+'/**N4VCustomElementsProd**/res/images')
- Update the FullURLCSSServer with the new webapp name (ex. URLNodeJSServer+':'+PORTTomcat+'/**N4VCustomElementsProd**/res/css')

5/ Duplicate the \Need4Viz\nodejs\apps_need4viz.json (for instance, name it **apps_need4vizProd.json**) and edit it :

- For each app, update the name (ex. "n4v_maps" -> "**Prod_**n4v_maps")
- For each app, update the script (ex. "".\\node_modules\\custom_element\\ce_libs\\n4v_maps.js" -> ".\\node_modules\\**custom_elementProd**\\ce_libs\\n4v_maps.js")
- For each app, update the out_file (ex. "..\\logs\\bi42\\n4v_maps_out.log" -> "..\\**logProd**\\bi42\\n4v_maps_out.log")
- For each app, update the err_file (ex. "..\\logs\\bi42\\n4v_maps_err.log" -> "..\\**logProd**\\bi42\\n4v_maps_err.log")

Now you can start your new instance of N4V running "**pm2 start apps_need4vizProd****.json**" in a PowerShell command.

To save both instances configuration (and make both of them restart after the server reboot), run a "**pm2 save"**command.

In the CMC, you can configure the 13 services on the new N4V instance ports range (8301 -> 8313).

[Full article](https://support.need4viz.com/kb/faq.php?id=125)

### How to install Node on a Linux server without accessing internet

#### Requirement

During the installation of N4V on a Linux server, an internet connexion may be necessary to install Node/nvm parts.

If the server has no internet access, you can authorize the following URLs to download manually the required files.

the URLS are :

[https://nodejs.org/dist/v20.20.2/node-v20.20.2-linux-x64.tar.gz](https://nodejs.org/dist/v20.20.2/node-v20.20.2-linux-x64.tar.gz)

[https://nodejs.org/dist/index.tab](https://nodejs.org/dist/index.tab)

[https://nodejs.org/dist/latest-v20.x/SHASUMS256.txt](https://nodejs.org/dist/latest-v20.x/SHASUMS256.txt)

[https://github.com/nvm-sh/nvm/archive/refs/tags/v0.40.1.tar.gz](https://github.com/nvm-sh/nvm/archive/refs/tags/v0.40.1.tar.gz)

#### Installation of the requirement

if you have already downloaded the files on a seperated server and transfered them you can skip this step

#### Download

```
mkdir ~/offline
cd ~/offline
curl -LO https://nodejs.org/dist/v20.20.2/node-v20.20.2-linux-x64.tar.gz
curl -LO https://nodejs.org/dist/index.tab
curl -LO https://nodejs.org/dist/latest-v20.x/SHASUMS256.txt
curl -LO https://github.com/nvm-sh/nvm/archive/refs/tags/v0.40.1.tar.gz
```

#### Offline installation

```
mkdir -p ~/.nvm

tar -xzf v0.40.1.tar.gz     -C ~/.nvm     --strip-components=1

echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.bashrc
echo '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"' >> ~/.bashrc

source ~/.bashrc
```

Final step

```
mkdir -p /tmp/node-mirror/v20.20.2
export NVM_NODEJS_ORG_MIRROR=file:///tmp/node-mirror

cp index.tab /tmp/node-mirror/
cp node-v20.20.2-linux-x64.tar.gz /tmp/node-mirror/v20.20.2
cp SHASUMS256.txt /tmp/node-mirror/v20.20.2/

nvm install 20.20.2
```

Now NodeJS and NVM are installed

[Full article](https://support.need4viz.com/kb/faq.php?id=127)

## MongoDB installation & upgrade

### MongoDB installation

#### Symptom

- MongoDB can be installed automatically with N4V but you can skip this installation.
- MongoDB is not mandatory for the using of N4V, it's only recommended to use it when you use Google Map geocoding (addresses resolution), to limit the cost of Google API.
- You can decide to install MongoDB after the initial installation of N4V.
- You can also decide to install MongoDB on a dedicated server for a clustered/split N4V deployment

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

1. If needed, download MongoDB setup [here](https://www.need4viz.com/support/file_download/e399a53bef664b73bc4f60aa300667b8/mongodb-windows-x86_64-4.4.19-rc0-signed.msi)
2. Install MongoDB on the N4V servers (or on a dedicated server)
3. If Mongo is installed on a separated server, after installation, open the mongod.conf file and update the **network interfaces**section. By default, only the local server (127.0.0.1 IP) can access the MongoDB instance so you need to add the IP of the server to authorize external servers to access the instance: After the update you need to restart the mongod service to apply the update.
4. Open the config.js file of your N4V server(s) and update the following properties to activate the using of MongoDB (**Use_MongoDB = true** and fill the **URLmongoDB**property with the **IP**of the mongoDB instance or **localhost**if MongoDB is installed on the N4V server then a name for the instance - N4V for example):
5. Restart the N4V services in a PowerShell windows by running the command "pm2 start all". Check in the logs (Need4Viz/logs) that there is no error. If the MongoDB instance is not accessible by the services, you'll find errors relative to the failed connection in the n4v_xxx_err.log files.

If the MongoDB service is installed on a dedicated server, you need to open the flow on port 27017 between the N4V server(s) and the MongoDB server.

[Full article](https://support.need4viz.com/kb/faq.php?id=90)

### MongoDB upgrade

#### Symptom

- MongoDB is a separate software optionally used with N4V.
- The version of MongoDB installed with N4V may vary depending on the N4V version you installed the first time (full installation).
- Following the procedure below, you will be able to upgrade the MongoDB instance on your N4V server.

#### Environment

- Windows Server
- Need4Viz : all versions

#### MongoDB Versions

The MongoDB version installed with the Full setup of N4V depends on the N4V version.

The end of life (EOL) of the MongoDB versions is described here : [https://www.mongodb.com/legal/support-policy/lifecycles](https://www.mongodb.com/legal/support-policy/lifecycles)

- N4V version
- N4V version 2023.0.1 -> 2024.3.0 = MongoDB version 4.4.19 (End of life : 02/2024)
- N4V version >= 2024.3.0 = MongoDB version 6.0.15 (End of life : 08/2026)

#### MongoDB upgrade principle

You can safely upgrade your MongoDB instance used with N4V following the below procedure.

To avoid any issues during the upgrade, please, respect exactly all the steps of the procedure.

For MongoDB upgrade, you cannot upgrade from any version to another one. You MUST pass through different intermediate upgrades. The complete procedure (all intermediate upgrades) is very fast but **all the indicated tasks must be done**.

Intermediate upgrades necessary : 4.2 -> 4.4 -> 5.0 -> 6.0 -> 7.0

#### MongoDB version used

To know which version of MongoDB is used on your N4V server :

1. Open a CMD window on your N4V server
2. Goto the \Need4Viz\MongoDB\Server\4.2\bin folder
3. Run the "mongod --version" command
4. Retrieve the MongoDB version

#### MongoDB upgrade from 4.2 to 4.4

This step is mandatory to upgrade from 4.2 to newer version of MongoDB (4.4, 5.0, 6.0, 7.0)

The end of life (EOL) of 4.2 version is April 2023.

The end of life (EOL) of 4.4 version is February 2024.

Platform Support of MongoDB 4.4 version :

- Windows Server 2019
- Windows Server 2016
- **Windows 2012 server is not supported**

Upgrade process to MongoDB 4.4 :

1. Download the **Need4Viz_setup_Update_MongoDB_4.4.exe** setup from the Download page of our Support site
2. Launch the upgrade setup of all Need4Viz server (where MongoDB is installed)
3. The setup should stop MongoDB and N4V on the server, upgrade MongoDB then restart automatically MongoDB and N4V.
4. Goto \Need4Viz\MongoDB\Server\4.2\bin folder and run "mongosh" (the default connection string should be OK -> mongodb://localhost) :
5. Check the MongoDB version is 4.4.19
6. Run the command : **db.adminCommand( { getParameter: 1, featureCompatibilityVersion: 1 } )**
7. If the version shown is '4.2', run the command : **db.adminCommand( { setFeatureCompatibilityVersion: '4.4' } )**
8. Open a Webi report and update a N4V component to check everything is working well

Once these steps are done, you have successfully updated your MongoDB instance from 4.2 to 4.4 version. You can now go to the next step to continue your update (to version 5.0)

#### MongoDB upgrade from 4.4 to 5.0

This step is mandatory to upgrade from 4.4 to newer version of MongoDB (5.0, 6.0, 7.0)

The end of life (EOL) of 5.0 version is October 2024.

Platform Support of MongoDB 5.0 version :

- Windows Server 2019
- Windows Server 2016

Upgrade process to MongoDB 5.0 :

1. Download the **Need4Viz_setup_Update_MongoDB_5.0.exe** setup from the Download page of our Support site
2. Launch the upgrade setup of all Need4Viz server (where MongoDB is installed)
3. The setup should stop MongoDB and N4V on the server, upgrade MongoDB then restart automatically MongoDB and N4V.
4. Goto \Need4Viz\MongoDB\Server\4.2\bin folder and run "mongosh" (the default connection string should be OK -> mongodb://localhost) :
5. Check the MongoDB version is 5.0.28
6. Run the command : **db.adminCommand( { getParameter: 1, featureCompatibilityVersion: 1 } )**
7. If the version shown is '4.4', run the command : **db.adminCommand( { setFeatureCompatibilityVersion: '5.0' } )**
8. Open a Webi report and update a N4V component to check everything is working well

Once these steps are done, you have successfully updated your MongoDB instance from 4.4 to 5.0 version. You can now go to the next step to continue your update (to version 6.0)

#### MongoDB upgrade from 5.0 to 6.0

This step is mandatory to upgrade from 5.0 to newer version of MongoDB (6.0, 7.0). You can also use it to upgrade an ancient 6.0 version of MongoDB to the latest version of 6.0.

The end of life of 6.0 version is July 2025.

Platform Support of MongoDB 6.0 version :

- Windows Server 2019
- Windows Server 2016

Upgrade process to MongoDB 6.0 :

1. Download the **Need4Viz_setup_Update_MongoDB_6.0.exe** setup from the Download page of our Support site
2. Launch the upgrade setup of all Need4Viz server (where MongoDB is installed)
3. The setup should stop MongoDB and N4V on the server, upgrade MongoDB then restart automatically MongoDB and N4V.
4. Open a Webi report and update a N4V component to check everything is working well

Once these steps are done, you have successfully updated your MongoDB instance from 5.0 to 6.0 version. You can now go to the next step to continue your update (to version 7.0)

#### MongoDB upgrade from 6.0 to 7.0

This step is mandatory to upgrade from 6.0 to newer version of MongoDB (7.0). You can also use it to upgrade an ancient 7.0 version of MongoDB to the latest version of 7.0.

The end of life (EOL) of 7.0 version is August 2027.

Platform Support of MongoDB 7.0 version :

- Windows Server 2022
- Windows Server 2019

Upgrade process to MongoDB 7.0 :

1. Download the **Need4Viz_setup_Update_MongoDB_7.0.exe** setup from the Download page of our Support site
2. Launch the upgrade setup of all Need4Viz server (where MongoDB is installed)
3. The setup should stop MongoDB and N4V on the server, upgrade MongoDB then restart automatically MongoDB and N4V.
4. Open a Webi report and update a N4V component to check everything is working well

Once these steps are done, you have successfully updated your MongoDB instance from 6.0 to 7.0 version.

[Full article](https://support.need4viz.com/kb/faq.php?id=94)

## N4V Services configuration

### How to manually start/stop Need4Viz services through command line

#### Symptom

- Start Need4Viz services from command line
- Stop Need4Viz services from command line

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

To start Need4Viz services :

1. Open a PowerShell command window as local administror of the server
2. Change directory to ***~Need4Viz_folder_installation/Scripts*/**
3. Run the **Start_Need4Viz.ps1** command
4. To check all services are started, run a **pm2 -list** command

To stop Need4Viz services :

1. Open a PowerShell command window as local administror of the server
2. Change directory to ***~Need4Viz_folder_installation/Scripts*/**
3. Run the **Stop_Need4Viz.ps1** command
4. To check all services are stopped, run a **pm2 -list** command

#### Possible issue

In case of restricted policy to execute scripts in the PowerShell window :

1. run the **set-executionpolicy unrestricted** command
2. answer **o** for the validation

[Full article](https://support.need4viz.com/kb/faq.php?id=8)

### How to repair Need4Viz services that cannot be stopped or started

#### Symptom

- Need4Viz services cannot be started/stopped manually or through the Central Configuration Manager.

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

To restart Need4Viz services :

1. Open the Central Configuration Manager and stop the BOEXI40Need4Viz service :
2. Open a PowerShell command window as local administror of the server
3. Check if services are stopped, run a **pm2 -list** command. You should get the following screen, if it's the case go to step 8 :
4. If services are started, you should get the following screen :
5. At this step, you can kill all the services with the **pm2 -kill** command. You should get after that the screen as in step 3. If some services are always running at this step, run again a **pm2 -kill** command (do not run a **pm2 -list** command after that).
6. Open the Windows task mananger and go to the Details tab. Kill manually all the residuals node.exe processes :
7. When no node.exe process is running in the Windows task manager, run a **pm2 -list** command. You should get the screen as in step 3.
8. Now you can start Need4Viz services through the Central Configuration Manager :
9. Check if services are started, run a **pm2 -list** command. You should get the following screen :

After these steps, you should be able to stop/start correctly the Need4Viz services through the Central Configuration Manager. **Close the PowerShell window**. You can check via the Windows Task Manager that the node services are correctly started/stopped :

You can do the same thing by using the scripts **Start_Need4Viz.ps1** and **Stop_Need4Viz.ps1** in the ***~Need4Viz_folder_installation/Scripts*/**directory.

#### Possible issue

In case of restricted policy to execute scripts in the PowerShell window :

1. run the **set-executionpolicy unrestricted** command
2. answer **o** for the validation

[Full article](https://support.need4viz.com/kb/faq.php?id=27)

### How to create or re-create the Need4Viz service

#### Symptom

- Need4Viz services have never been created

OR

- Need4Viz services cannot be started/stopped through the Central Configuration Manager.

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

1. Open a PowerShell command window as local administror of the server. If Need4Viz services have never been created, go to step **11**.
2. Open the Central Configuration Manager and stop the BOEXI40Need4Viz service :
3. Check if services are stopped, run a **pm2 -list** command. You should get the following screen, if it's the case go to step 7 :
4. If services are started, you should get the following screen :
5. Run the **Stop_Need4Viz.ps1** command in the ***~Need4Viz_folder_installation/Scripts*/**directory.
6. Run a **pm2 list** command. You should get the screen as in step 3.
7. Run a **pm2 kill**command.
8. Open a Command Prompt and run the command **sc delete boexi40need4viz.exe** :
9. Check in the Central Configuration Manager that the Need4Viz service does not exist anymore :
10. Open the folder ***~Need4Viz\nodejs\node_modules\pm2-windows-service\src\daemon***and delete all files in it
11. In the PowerShell window, run the **Create_Need4Viz_Service.ps1** in the ***~Need4Viz_folder_installation/Scripts*/**directory, answer "n" to the prompt :
12. Check if services are started, run a **pm2 list** command. You should get the following screen :
13. Check in the Central Configuration Manager that the service is correctly created :

After these steps, you should be able to stop/start correctly the Need4Viz services through the Central Configuration Manager. **Close the PowerShell window**. You can check via the Windows Task Manager that the node services are correctly started/stopped :

#### 

#### Possible issue

In case of restricted policy to execute scripts in the PowerShell window :

1. run the **set-executionpolicy unrestricted** command
2. answer **o** for the validation

[Full article](https://support.need4viz.com/kb/faq.php?id=28)

### Windows Service Wrapper error when creating N4V Service

#### Symptom

- After execution of the script Create_Need4Viz_service.ps1, N4V Service does not appear in the CCM and the following errors are displayed :

#### 

#### 

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

The Need4Viz service created in the CCM needs the Microsoft .NET Framework 3.5 to run correctly.

Even if the .NET Framework 4 is already installed on the Need4Viz server, you need to install the .NET Framework 3.5 too.

[Full article](https://support.need4viz.com/kb/faq.php?id=41)

## Global N4V configuration

### How to increase number of rows accepted by components

#### Symptom

- When feeding components with more than a predefined number of rows, an alert message saying the limit of rows is reached for this component is displayed instead of the chart.
- The message displayed is "Maximum input lines allowed for this chart"

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

Each N4V component is limited to a specific number of rows as input. This limitation is done to avoid overloading of the component in the web browser.

Indeed, unlike Webi's pagination mode (which only loads in the browser the rows displayed on the actual page), the N4V components embed all the input rows available in the bloc.

There is another limitation : Webi limit the number of rows to send to an external engine (N4V for example) to 50.000 rows, that's why you cannot send more than 50.000 rows to a N4V component, even if you define a greater limit with the following method.

To change/update the limit number of rows accepted by a N4V component, choose a method (A, B or C in the above list) and follow the steps on each N4V server :

**A/ Update directly in the config.js file**

1. Open the file **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config_charts.js**
2. For each component, there is a setting named ***component*_limit_lines** that define the limit of rows accepted by the component
3. Find the corresponding component you want to update. For instance, to update the limit for the **Pivot Table** component, find the **pivottable_limit_lines** setting and change the value from 10.000 to the value you want (above 50.000)
4. Save the file
5. Open a PowerShell command window as local administror of the server
6. Run the **Stop_Need4Viz.ps1** command in the ***~Need4Viz/Scripts*/**directory
7. Then run the **Start_Need4Viz.ps1** command in the ***~Need4Viz/Scripts*/**directory.

**B/ Update from the N4V Web Admin Portal**

1. Connect to the N4V Web Admin Portal (for instance, if you are using the ports 8101-8113 for N4V, on your N4V server, open a browser and connect to the URL http://localhost:8101/admin)
2. On each tab (one for each N4V service), change the appropriate Row limit
3. Update the new configuration on each tab :
4. Restart the N4V services :

**C/ Update the row limit on individual chart in your Webi report**

Since N4V 2025.2 you can change directly on a specific chart in Webi the row limit for the current rendering :

You can go ahead of the global row limit defined for the component (just for this chart in your report, this change will not update the global row limit).

Once you have updated the row limit following method A, B or C, you can turn a Webi bloc with more than 10.000 rows into a Pivot Table, the component is correctly displayed.

#### Possible issue

Try to update progressively for each component the number of rows depending on your needs. The more the number of rows and column will be huge in the bloc, the higher will be the risk to overload the web browser of the user.

As a second issue possible, if you build a dashboard with many component in the same page and a huge number of rows/columns for each components, the web browser may be overloaded when trying to display the dashboard.

[Full article](https://support.need4viz.com/kb/faq.php?id=39)

### How to hide N4V components in the list of available charts in Webi

#### Symptom

- You want to disable some N4V components from the list of Webi charts.

#### Environment

- Need4Viz : all versions

#### Resolution

Each N4V component can be enabled/disabled through a specific parameter.

To disable a N4V component, follow the steps on each N4V server :

1. Open the file **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config_charts.js**
2. For each component, there is a setting named ***component*_activate** that define if the component is visible or not in the Webi list of charts
3. Find the corresponding component you want to disable. For instance, to hide the **Pivot Table** component, find the **pivottable_activate** setting and change the value from **true**to **false**
4. Save the file
5. Open a PowerShell command window as local administror of the server
6. Run the **Stop_Need4Viz.ps1** command in the ***~Need4Viz/Scripts*/**directory
7. Then run the **Start_Need4Viz.ps1** command in the ***~Need4Viz/Scripts*/**directory.

Now open a Webi document and display the list of aailable charts, the N4V component is displayed anymore.

#### Other resolution

As another possibility, you can also open the N4V Administration Console and tick/untick the according component to display/hide it in the Webi library :

#### 

#### Other resolution

If the component you want to hide is the only one of its family (for instance, RDF chart) or if a complete family needs to be hidden, then disable the corresponding service in the CMC / Webi Application :

Save and exit. In Webi, the corresponding chart family will not be displayed anymore.

[Full article](https://support.need4viz.com/kb/faq.php?id=42)

### Which log/work files can be deleted regularly

#### Symptom

- As for many other softwares, N4V and its components use some files to log or to work. Those files may grow over time and it may be necessary to delete them.

#### Environment

- Windows Server
- Need4Viz : all versions

#### Resolution

The following files can be deleted manually or automatically (through a custom script you can create) :

- \Need4Viz\logs\n4v_xxx_out__*timestamp*.log (rotate logs system generates one file a day)
- \Need4Viz\logs\n4v_xxx_err__*timestamp*.log (rotate logs system generates one file a day)

The working directory of N4V is used each time a chart is rendered to be printed. It can be emptied regularly :

- \Need4Viz\nodejs\node_modules\custom_element\ce_works\*

If MongoDB is used, you can also delette regularly the following log file (you can delete the file even if mongodb is running, a new log file will be recreate automatically when the service is restarted) :

- \MongoDB\Server\4.2\log\mongod.log

[Full article](https://support.need4viz.com/kb/faq.php?id=43)

### How to configure N4V for viewing N4V elements in Webi from outside & inside entreprise network

#### Symptom

- N4V for Webi is successfully installed and all components can be used/viewed in Webi inside your entreprise network.
- Your Webi platform is also available from outside your entreprise network (public internet or extranet) but N4V components cannot be viewed correctly from this external access.

#### Environment

- Windows / Linux Server
- Need4Viz : all versions

#### Resolution

The N4V components are generated in HTML format from N4V services and sent to Webi to be included in IFrames.

The generated HTML contains some links to N4V static libraries (.js files) called directly from the Web browser of the user.

It's mandatory that the static N4V webapp is deployed on a web application server (for instance Tomcat) that can be reached from outside and inside through the same URL link.

For instance, if the BOE instance is visible from outside entreprise network with the URL **https://my_outside_URL/BOE/BI** and from inside entreprise network with the URL **http://my_inside_URL/BOE/BI** you need to check that :

- N4VCustomElements webapp can be reached from outside with the URL **https://my_outside_URL/N4VCustomElements**. To check that, try to display the **https://my_outside_URL/N4VCustomElements/res/images/green_tick.png** image in a browser session from outside your entreprise network : it should display correctly a green tick image.
- N4VCustomElements webapp can be reached from inside with the same URL as for external access : **https://my_outside_URL/N4VCustomElements**. To check that, try to display the **https://my_outside_URL/N4VCustomElements/res/images/green_tick.png** image in a browser session from inside your entreprise network : it should display correctly a green tick image.

If previous tests are OK then

- Open the file **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js**
- Change the **URLNodeJSServer**to value '**my_outside_URL**'
- Change the **PORTTomcat** to value **443**(for example)
- Open a powershell window and run "pm2 start all" to restart all N4V services with the new confguration
- View your Webi report with N4V components from inside and outside your entreprise network

[Full article](https://support.need4viz.com/kb/faq.php?id=51)

### External web access used by N4V server

#### Symptom

- When printing a Webi report in PDF/XLS format, some N4V components are not correctly printed (a puzzle may appear) or there is a very long delay to print the report.
- When using Google Address component (geolocation), the component is not displayed correctly.

#### Environment

- Windows & Linux Server
- Need4Viz : all versions. Fixed in 2022.0.1 version.

#### Resolution

Depending on the action and the N4V components, the N4V server may need to access internet.

When printing a Webi report containing the following N4V components :

- Simple Sankey
- Google Maps Lat/Lon
- Google Maps Geocoding
- Google Heatmap
- OpenStreetMap Chart Pie

When displaying a Webi report containing the following N4V component :

- Google Maps Geocoding

The URL accessed from the N4V server are the following :

- [https://www.google.com/jsapi](https://www.google.com/jsapi)
- [https://*.googleapis.com](https://maps.googleapis.com)
- [https://*.gstatic.com](https://www.gstatic.com)
- [https://*.openstreetmap.org](https://a.tile.openstreetmap.org)

***A. If no external web access is allowed from the N4V server***

Set to **true** the **NoExternalWebAccessAllowed**variable in the **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js** file, so a blank frame with unprintable message will be generated instead of the expected render.

***B. If external web access is allowed through a proxy from the N4V server***

Set in the **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js** file the **ProxyHost** variable (only proxy without authentication can be used).

***C. If external web access is allowed directly from the N4V server***

You have nothing to do.

**Notice :**

After each update of the config.js file, follow these steps to make the changes effective :

1. Open a PowerShell command window as local administror of the server
2. Change directory to ***~Need4Viz_folder_installation/Scripts*/**
3. Run the **Start_Need4Viz.ps1** command

[Full article](https://support.need4viz.com/kb/faq.php?id=54)

### How to customize global look & feel of N4V elements for the entire company

#### Symptom

- You want to customize globally some items (button colors, fonts...) of all N4V components for all your company.

#### Environment

- Need4Viz : 2024.1+

#### Resolution

You can use a CSS customization file (custom.css) that is automatically embeded in all N4V component.

This file will help you to overload the look & feel of many items in N4V elements, defining them in one place.

The custom.css file is located in the N4VCustomElements webapp (generally hosted on your SAPBI tomcat web server), in the following folder : N4VCustomElements\res\css\custom\custom.css

In the 2025.1+ version of N4V, a sample is provided (custom_sample.css). You can try and adapt the content of this file (copy/paste it in the custom.css file) to help you defining your own custom rendering style.

In this sample, you can define 2 colors :

- The **main background color of buttons & popup** : use RGB component values to define your own color (as provided in example)
- The **default buttons text color** : use a Hexa value (as provided in example)
- All the depending colors will be automatically calculated

You don't need to restart N4V server (neither the Tomcat server). Just refresh the cache of your browser and the update will be immediately viewable.

The custom.css file is always automatically embedded in all N4V widgets but, sometime, the style of some items are overloaded by the settings you can choose in the Extended Parameters. You may need to make some test and use tricks & tips to enforce the usage of style defined in the custom.css file (for instance, you may need to add an "**!important**" tag to overload the style) :

[Full article](https://support.need4viz.com/kb/faq.php?id=116)

## SAPBI CMC Configuration

### Errors on configuration N4V services in the CMC

#### Symptom

- Need4Viz services are started correctly (no error in n4v_xxx_err.log files)
- Need4Viz services cannot be declared in the SAPBI CMC.

#### Environment

- Need4Viz : all versions

#### Resolution

In some cases, Need4Viz services cannot be declared in the CMC.

**1/ Check if the your SAPBI version is not flagged as a defect version here :**

[https://www.need4viz.com/support/kb/faq.php?id=35](https://www.need4viz.com/support/kb/faq.php?id=35)

**2/ If the error encountered is the following one :**

Check if your N4V key is activated :

- Open the URL http://xxxx:8209/about to see if the key is activated
- Check the files n4v_xxx_out.log in ***~Need4Viz_folder_installation/logs***folder, you should have a message concerning the validity of the key

If your key is expired, contact our sales team to get a new one.

Once you have a new key.js file :

1. Replace the existing one in the **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\** folder
2. Open a PowerShell command window as local administror of the server
3. Change directory to ***~Need4Viz_folder_installation/Scripts*/**
4. Run the **Start_Need4Viz.ps1** command

**3/ In case of other error :**

1. Check the URL used to declare the service is correctly whitelisted (cf. installation guide of N4V)
2. Check the port used to declare the service is corresponding to the ports defined in the config.js file (in the **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\** folder)
3. Check the flows (for instance 8201, 8202...) are opened between your tomcat (SAPBI) server in N4V server

[Full article](https://support.need4viz.com/kb/faq.php?id=55)

### How to retrieve N4V services names from a previous configuration

#### Symptom

- After a SAPBI upgrade, the Need4Viz services are not anymore declared in the SAPBI CMC
- Need4Viz services are installed and started correctly

#### Environment

- Need4Viz : all versions
- SAPBI : all version BI 4.2 & 4.3

#### Resolution

In some cases, after a SAPBI upgrade, the Need4Viz services previously declared in the CMC are not anymore visible. You need to recreate the 13 N4V services (custom elements) in the CMC with **exactly the same name** as previously to make your Webi reports including N4V elements working.

If you haven't saved in a document the names used in your previous installation, you can check the following steps to retrieve them

**1/ Default naming**

In a default N4V installation, a file containing default names you can use is installed in the ~Need4viz installation folder.

Open the **README.txt** file in the **~Need4viz** installation folder, the list of services is described. By default, this is the list you should find (the ports 81xx may change accordingly to your own settings) :

- Service Name = **N4V GeoMaps** | Service URL = [http://your.tomcat.url:8101](http://your.tomcat.url:8101/) - Service Name = **N4V Gauges** | Service URL = [http://your.tomcat.url:8102](http://your.tomcat.url:8102/) - Service Name = **N4V Bars** | Service URL = [http://your.tomcat.url:8103](http://your.tomcat.url:8103/) - Service Name = **N4V Circulars** | Service URL = [http://your.tomcat.url:8104](http://your.tomcat.url:8104/) - Service Name = **N4V Times** | Service URL = [http://your.tomcat.url:8105](http://your.tomcat.url:8105/) - Service Name = **N4V Relations** | Service URL = [http://your.tomcat.url:8106](http://your.tomcat.url:8106/) - Service Name = **N4V Trees** | Service URL = [http://your.tomcat.url:8107](http://your.tomcat.url:8107/) - Service Name = **N4V Tiles** | Service URL = [http://your.tomcat.url:8108](http://your.tomcat.url:8108/) - Service Name = **N4V MultiGraph** | Service URL = [http://your.tomcat.url:8109](http://your.tomcat.url:8109/) - Service Name = **N4V Tables** | Service URL = [http://your.tomcat.url:8110](http://your.tomcat.url:8110/) - Service Name = **N4V RDF** | Service URL = [http://your.tomcat.url:8111](http://your.tomcat.url:8111/) - Service Name = **N4V Gantt** | Service URL = [http://your.tomcat.url:8112](http://your.tomcat.url:8112/) - Service Name = **N4V Navigation** | Service URL = [http://your.tomcat.url:8113](http://your.tomcat.url:8113/)

**2/ Retrieve the names with a Webi report**

If the default names are not working, the other solution to retrieve the previous N4V services names is to open WID files containing N4V elements and get the name of the services.

Get the name of a Webi report containing N4V elements and, in the CMC, retrieve the wid File name of the report :

On the SAPBI server, in the filestore (by default, it is in ***~Installation_SAPBI*/SAP BusinessObjects Enterprise XI 4.0\FileStore\Input\...** folder), retrieve the .wid file and copy it in a temporary folder (do not try to open the initial version of the wid, always work on a copy).

Rename the copy of your .wid report with the extension .zip then extract the archive.

In the extracted archive, open in Notepad++ the file **DOCSPEC**in the **Data/RE/** folder.

In the file, search the tag **PLUGINFO NAME=“com.sap.webi.rscustomelement”** then **CUSTOM_ELEMENT**... You should then find the N4V Services names used to build the N4V elements in the Webi report.

You now just have to recreate the services in the CMC, activate them then save.

Now, you should be able to display the N4V elements, after a refresh of your Webi report.

[Full article](https://support.need4viz.com/kb/faq.php?id=88)

## Printing N4V components

### How to enable printing (pdf/xls) of N4V components

#### Symptom

- When printing a Webi report in PDF/XLS format, some N4V components are not correctly printed (a puzzle may appear) or there is a very long delay to print the report.

#### Environment

- Windows & Linux Server
- Need4Viz : all versions. Fixed in 2022.0.1 version.

#### Resolution

Depending on the N4V components printed, the N4V server may need to access internet and/or reach the URL used to access the N4VCustomElements webapp.

***A. Components which require an internet access (Simple Sankey; Google maps, OpenStreetMaps)***

When printing Webi report containing some N4V components (Sankey, OpenStreet & Google maps components), the N4V server needs to access internet to build the chart and provide a PNG file to Webi (to generate the PDF/XLS final file). If the N4V server has no access to internet, the PNG image file cannot be generated and a long timeout can be reached before a puzzle image is rendered (default image).

To avoid this, two possibilities are offered :

**1. It's impossible to set an internet acces to the N4V server**

In this case, the PNG images for the corresponding N4V components will never be generated. To avoid the puzzle image and waiting timeout, just set to **true** the **NoExternalWebAccessAllowed**variable in the **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js** file, so a blank frame with unprintable message will be generated instead of the expected render.

**2. An internet access can be set on the N4V server through a proxy :**

In this case, you can set in the **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js** file the **ProxyHost** variable (only proxy without authentication can be used)

**For both solutions**, once the config.js file is updated and saved, you need to restart the N4V services through the following steps :

1. Open a PowerShell command window as local administror of the server
2. Change directory to ***~Need4Viz_folder_installation/Scripts*/**
3. Run the **Start_Need4Viz.ps1** command

After that, try to print a Webi report including an impacted N4V component (Sankey, OpenStreet or Google map), the chart should be correctly render in the final PDF/XLS file.

The following URLs must be accessible from the N4V server to print correctly the corresponding N4V components :

**Sankey :** [https://www.google.com/jsapi](https://www.google.com/jsapi) [https://www.gstatic.com/charts](https://www.gstatic.com/charts)**Google maps :** [https://maps.googleapis.com](https://maps.googleapis.com/) [https://www.gstatic.com/charts](https://www.gstatic.com/charts) [https://fonts.gstatic.com](https://fonts.gstatic.com/) [https://maps.gstatic.com](https://maps.gstatic.com/)**OpenStreetMap :** [https://*.openstreetmap.org](https://%2A.openstreetmap.org/)

B. Components which not require an internet access

When printing Webi report containing some N4V components other than Simple Sankey, OpenStreet or Google maps components, it may arrive than the renderer is a puzzle (after a long delay). Mlost of the time, this is due to an access error from the N4V server to the URL used to access the N4VCustomElements static webapp (for instance, configuration of the server behind a proxy).

To avoid this, two possibilities are offered :

**1. Disable****proxy for the N4V server**

In this case, the server will be able to access directly the URL defined in the **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js** file by the parameters **URLNodeJSServer& PORTTomcat**without passing through a proxy.

**2. Enable N4VCustomElements****URL** **in your proxy**

In this case, you need to configure your proxy to authorize the N4V server to access the URL defined in the **~Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js** file by the parameters **URLNodeJSServer& PORTTomcat.**

Then in the **config.js** file, configure the parameter ProxyHost parameter with your proxy information. Proxy authentication has to be anonymous (authentication with credentials is not supported for the printing of the N4V components).

[Full article](https://support.need4viz.com/kb/faq.php?id=40)

### Issue when printing Webi report included N4V components on a Linux deployment

#### Symptom

- When printing a Webi report in PDF/XLS format, some N4V components are not correctly printed (a puzzle may appear) or there is a very long delay to print the report.
- This error only appears in Linux N4V deployment

#### Environment

- Linux Server
- Need4Viz : all versions

#### Resolution

To install the N4V solution on a Linux server, a proxy configuration has been used (to get from internet the modules used by N4V).

After the installation, the proxy configuration must be deleted to enable the correct printing of N4V components.

To fix the issue, follow the steps :

1. Delete the environment variables **http_proxy** et **https_proxy** from the .bashrc profile
2. Source again the .bashrc profile to be sure the variables are not loaded in the profile
3. Test a CURL command to be sure the proxy is not set (CURL should give an error)
4. run "**pm2 stop all**" to stop all the N4V services
5. run "**pm2 kill**" to stop the pm2 deamon
6. run "**pm2 start apps_ce.json**" to launch again the pm2 daemon (and run the N4V services)
7. Print again your Webi report included N4V components

[Full article](https://support.need4viz.com/kb/faq.php?id=50)

### Issue when printing Webi report included N4V components

#### Symptom

- When printing a Webi report in PDF/XLS format, some N4V components are not correctly printed (a puzzle may appear) or there is a very long delay to print the report.
- In the N4V logs (#Need4Viz/logs/n4v_xxx_err.log), the following error appears :

Error: Failed to launch the browser process! [18652:8652:0927/113256.289:ERROR:cache_util_win.cc(21)] Unable to move the cache: Access Denied. (0x5) [18652:8652:0927/113256.289:ERROR:cache_util.cc(138)] Unable to move cache folder C:\Program Files (x86)\Need4Viz\nodejs\**PuppeteerDataDir**\ShaderCache\GPUCache to C:\Program Files (x86)\Need4Viz\nodejs\PuppeteerDataDir\ShaderCache\old_GPUCache_000 [18652:8652:0927/113256.289:ERROR:disk_cache.cc(184)] Unable to create cache [18652:8652:0927/113256.289:ERROR:shader_disk_cache.cc(606)] Shader Cache Creation failed: -2

#### Environment

- Windows & Linux Server
- Need4Viz : all versions

#### Resolution

**A/ Temp data folder not accessible**

The N4V engine use the Puppeteer module (based on Chrome) to generate a PNG image sent to Webi for the PDF/XLS printing. Puppeteer use a working folder and sometime, this folder is not anymore accessible by the module.

To fix the issue, follow the steps :

1. Entirely delete the **PuppeteerDataDir** folder (in the error logs, you should find the full path, generally it is ~Need4viz/nodejs/**PuppeteerDataDir**)
2. Launch a Powershell window as administrator
3. Run the command "pm2 start all" to restart all the N4V services
4. Try to print again your Webi report

**B/ Chart too large for printing**

Sometime, when the component to print is a HTML scroll table (for instance), the html generated can be very huge (several megabytes) caused by the hight number of lines in the table (several thousands). In this case, the printing engine may have some difficulties to print the rendering of the HTML.

To fix the issue, reduce the number of lines of the table to print it.

[Full article](https://support.need4viz.com/kb/faq.php?id=56)

### Configuration of N4V for printing components (PDF/XLS export from Webi)

#### Symptom

- When printing a Webi report in PDF/XLS format, N4V components may not be correctly printed (a puzzle may appear) or there is a very long delay to print the report.

#### Environment

- Linux/Windows Server
- Need4Viz : all versions. New settings available in 2024.3.0.

#### Resolution

To print a PNG of a N4V component (used when printing a Webi report in PDF/XLS), N4V server needs to access the N4VCustomElements webapp (generally deployed on your SAPBI Tomcat). The URL used to access this webapp may not be available from the N4V server (URL only available from the user's browser).

In version 2024.3.0, new settings have been created to dynamicaly change the URL of the N4V webapp when the component is print on the N4V server.

For instance, if Tomcat is installed on the same server as the N4V server (and accessible on port 8080), you can change the settings in the \Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js file as following :

**var use_internal_webapp_PRINT = true; var URL_PORT_WebApp_int_PRINT = "http://localhost:8080";**

Another example, if Tomcat is deployed on a second server accessible from the N4V server by its name (and accessible on port 80), you can set the \Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js file as following :

**var use_internal_webapp_PRINT = true; var URL_PORT_WebApp_int_PRINT = "http://*server_name*";**

One the config.js file is updated, save it and restart all N4V services (run a "pm2 start all" command in a PowerShell window run as administrator) and try to print again your report.

[Full article](https://support.need4viz.com/kb/faq.php?id=110)

## SAPBI Migration (4.2 to 4.3)

### Previous chart settings are not displayed after a migration on a new Need4Viz server

#### Symptom

- Need4Viz was previously installed on a first server (for instance in a SAPBI 4.2 environment) and dashboards have been designed with Need4Viz components
- A new server is installed with a full setup of Need4Viz (for instance in a SAPBI 4.3 environment) and the BO reports are migrated from the previous installation to the new one.
- When opening the dashboards in the new SAPBI environment, the Need4Viz components are correctly displayed but when opening the setting parameters, all the custom parameters are re-initialized (for instance, the title setting of the chart is empty and trying to set a new one has no effect).

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects Business Intelligence Platform all version
- Need4Viz : from 2021.4.1 full setup installation

**Cause:**

- A new general configuration setting has been added in the 2021.4.1 version (and upper). This setting give the ability to keep common parameters between Need4Viz charts (of a same category) when doing a "turn into".
- This setting cannot be activated when previous version of Need4Viz have been used.
- This setting is automatically set when installing a full version of Need4Viz (from the 2021.4.1 version).
- During a Patch installation, this setting is not changed (all patchs applied on a full setup keep the previous value)

#### Solution

Considering a **source environment** with a Need4Viz installation (for instance SAPBI 4.2) and a **target environment** with a new Need4Viz installation (for instance SAPBI 4.3). After installation of Need4Viz full setup in the target environment :

- Open the ***~Need4Viz_folder_installation*/nodejs/node_modules/custom_element/ce_libs/config.js**file in the **source env**.
- Check the value of the ***Use_Common_RegId*** setting (true or false)
- Close the file.
- Open the ***~Need4Viz_folder_installation*/nodejs/node_modules/custom_element/ce_libs/config.js**file in the **target env**.
- Set the value of the Use_Common_RegId setting with the same value as in the **source env**(probably "false")
- Save and close the file
- Restart the Need4viz server in the **target env.** with the script ***~Need4Viz_folder_installation*/scripts/Start_Need4Viz.ps1** in a PowerShell window
- Open a migrated dashboard in the **target env.** and check the settings of a Need4Viz component, they should be correctly displayed now.

[Full article](https://support.need4viz.com/kb/faq.php?id=33)

### Migrate Need4Viz infrastructure during a SAPBI migration (ex. 4.2 to 4.3) - ON THE SAME SERVER

#### Symptom

- The SAPBI environnement will be upgraded from a 4.2 version to a 4.3 version WITHOUT CHANGING SERVER
- Need4Viz is already installed and configured on the SAPBI server

#### Environment

- Windows/Unix Server
- Need4Viz : all versions

#### Resolution

1. **Before upgrading SAPBI version**, make a backup of the full **/tomcat/webapp/N4VCustomElements** folder.
2. Open the **CMC / Applications / Web Intelligence / Custom Elements** :
3. For each service, click on "Configure..." and copy/paste the Service Name & Service URL values in a **text file** to backup the exact names and URL of each service :
4. **Make your SAPBI upgrade** to the final version (ex. 4.3SP2)
5. After the upgrade, check the **/tomcat/webapp/N4VCustomElements** folder and, if it doesn't exist anymore, copy the previous backuped version (step 1)
6. Open a PowerShell window and run "pm2 list" to check all N4V services are up and running :
7. Open the **CMC / Applications / Web Intelligence / Custom Elements**and check all the N4V services are configured. If no service is defined, recreate all the services with exactly the same name & URL as backuped in the text fil in step 3 (be careful to previously whitelist the URLs if necessary)
8. Once the services are configured in the CMC, you could open a Webi report including existing N4V charts and chek it is correctly displayed.
9. At these step, if your N4V version is prior to 2021.12.4, the navigation components and native Webi Linking Element will not work on the SAPBI 4.3SP2 version, goto the next paragraph to update your N4V version.

#### Update N4V version for 4.3SP2

Once your SAPBI version is updated and your N4V version is prior to 2021.12.4, you have to update your N4V version to enable the navigation (components and Webi linking elements) in Webi :

1. Open **Need4Viz\nodejs\node_modules\custom_element\ce_libs\config.js**file
2. Change the “SAPBI_ver” setting from “42” to “43”
3. Open a PowerShell command and run “pm2 stop all” then “pm2 start all”

[Full article](https://support.need4viz.com/kb/faq.php?id=37)

### Migrate Need4Viz infrastructure during a SAPBI migration (ex. 4.2 to 4.3) - ON A NEW SERVER

#### Symptom

- A new SAPBI environnement (4.3) will be installed on a NEW SERVER and data will be migrated with live to live mode (from 4.2 to 4.3)
- Need4Viz is already installed and configured on the initial SAPBI server (**SOURCE**)
- Need4Viz is not installed on the new target SAPBI server (**TARGET**)

#### Environment

- Windows/Unix Server
- Need4Viz : all versions

#### Resolution

1. Download the N4V 2021.12.4 **Patch**setup in your Support Download Center and install it on the **SOURCE**environement
2. After the Need4Viz upgrade, check everything is OK in existing Webi reports including N4V components in the 4.2 environnement
3. Install the 4.3 SAPBI environnement on the **TARGET** server. Install Need4Viz in the exact same directory as on the **SOURCE**system.
4. Download the N4V 2021.12.4 **Full**setup in your Support Download Center and install it on the **TARGET**environement. Do not perform the creation of Need4viz service at this step. Do not start Need4Viz.
5. Copy the full content of the **/tomcat/webapp/N4VCustomElements** folder from the **SOURCE**environnement and paste it in the **/tomcat/webapp/N4VCustomElements** folder of the **TARGET**environnement. This action will transfer all your cutom maps and files from 4.2 to 4.3 system.
6. Copy the full content of the **~Need4Viz/node/nodejs/node_modules/custom_element/ce_libs, ce_settings & ce_icons** folders from the **SOURCE**environnement and paste it in the ~**Need4Viz/node/nodejs/node_modules/custom_element/**folder of the **TARGET**environnement. This action will tranfer all custom files (config, palettes, list maps,...) from 4.2 to 4.3 system.
7. Edit the **~Need4Viz/node/nodejs/node_modules/custom_element/ce_libs****/config.js** file on the **TARGET**system and check the following parameters :
  1. ***URLNodeJSServer***: update this setting with the SAPBI 4.3 Tomcat URL
  2. ***PORTTomcat***: update this setting with the SAPBI 4.3 Tomcat port
  3. ***LocalCEPath***: if Need4Viz has been installed in a different path location as SOURCE system, update this setting with the correct path
  4. ***LogUsageFile***: if Need4Viz has been installed in a different path location as SOURCE system, update this setting with the correct path
  5. ***SAPBI_ver***: For a SAPBI 4.3, fill with value **43**
8. Create the Need4Viz service (with the **~****Need4Viz/scripts/Create_Need4Viz_Service.ps1** script).
9. Open a PowerShell window and run "pm2 list" to check all N4V services are up and running :
10. Open the **CMC / Applications / Web Intelligence / Custom Elements** in the **TARGET**system and recreate all N4V services with exactly the same names as in the **SOURCE**system (be careful to previously whitelist the URLs if necessary) :
11. Once the services are configured in the CMC, you could open a Webi report imported form SAPBI 4.2 system and including existing N4V charts and chek it is correctly displayed.

[Full article](https://support.need4viz.com/kb/faq.php?id=38)
