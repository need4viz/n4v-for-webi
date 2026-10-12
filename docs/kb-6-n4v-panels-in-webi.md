# N4V Panels in Webi – N4V FOR WEBI Knowledge Base

Troubleshooting and how-to articles from the official [Need4Viz Support Knowledge Base](https://support.need4viz.com/kb/), category 6. Each entry gives the symptom, context and resolution; the full article with screenshots is linked below it. Back to the [Knowledge Base index](knowledge-base.md).

## Configure N4V Panels

### How to activate the N4V Panel (Webi extensions)

#### Symptom

- You want to activate the N4V Webi extensions provided by Need4Viz to enhance the Webi capabilities

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.3 SP3+
- N4V 2024.1.0+

#### **Resolution**

The goal of this article is to activate the N4V extensions provided by Need4Viz (starting from N4V 2024.1.0 release).

The extensions can only be used in a SAPBI 4.3 SP3+ environment. Some features in the N4V Panel are only working in 4.3SP4+ environment.

Two distinct extensions are provided by Need4Viz : the user extension and the designer extension.

**1. The user extension**

This extension give the end user the ability to export in HTML and/or in PDF the full current page of the report (or each individual N4V element), directly on his computer.

Once activated for the user's group in the CMC, the user will see the HTML / PDF icons (both in Design and in Reading mode) in Webi :

To activate this extension, the URL to declare in the CMC is **[http://localhost/N4VCustomElements/extension/Need4Viz/webi_apps/](http://localhost/N4VCustomElements/extension/Need4Viz/webi_apps/)user_app/extension.json** (see below for the details)

**2. The designer extension**

This extension give the Webi designer user the ability to access the Chart Recommender, the N4V SVG tool and the N4V Palette tool.

Once activated for the user's group in the CMC, the designer user will see the Chart recommender, SVG and Palette icons (both in Design and in Reading mode) in Webi :

To activate this extension, the URL to declare in the CMC is **[http://localhost/N4VCustomElements/extension/Need4Viz/webi_apps/](http://localhost/N4VCustomElements/extension/Need4Viz/webi_apps/)design_app/extension.json** (see below for the details)

3. How to activate the extensions

Log in to the CMC.

"In the Application / Web Intelligence / Authorized URLs" panel, add the **http(s)://xxxxxxxx/N4VCustomElements** URL :

Assignment of an extension to a users group : Choose the users group who will be able to use the extension and right clic to "Customization".

It is highly recommended to create 2 distinct groups in the CMC, dedicated to the N4V extensions :

The first group will be able to see only the user extension, the second group will see both user and designer extension.

Then affect the related extensions to each of those groups.

Clic on "Extensions" tab the "Add" :

If the N4VCustomElements webapp is deployed on the SAPBI Tomcat server, fill the following URL (generally you'll need to replace the [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) by the https URL of the N4VCustomElements deployment) :

**[http://localhost/N4VCustomElements/extension/Need4Viz/webi_apps/user_app/extension.json](http://localhost/N4VCustomElements/extension/Need4Viz/webi_apps/user_app/extension.json)**(or****[http://127.0.0.1/N4VCustomElements/extension/Need4Viz/webi_apps/user_app/extension.json](http://127.0.0.1/N4VCustomElements/extension/Need4Viz/webi_apps/user_app/extension.json)****)

The user extension is located in **http(s)://xxxxxxxx/N4VCustomElements/extension/Need4Viz/webi_apps/user_app/extension.json**

The designer extension is located in **http(s)://xxxxxxxx/N4VCustomElements/extension/Need4Viz/webi_apps/design_app/extension.json**

Clic on "I accept the risk" then clic "OK"

Activate the extension(s) (tick the extensions) then Save and Close the popup.

Log in to SAPBI with a user account included in the updated group. Open a Webi report and check in the right panel the Extensions button:

Click on the button, then N4V extension panel is displayed :

[Full article](https://support.need4viz.com/kb/faq.php?id=91)

### Issue when adding the N4V extension in HTTPS environment

#### Symptom

- You want to activate the N4V Webi extensions provided by Need4Viz to enhance the Webi capabilities but the extension is hosted on a Tomcat configured in HTTPS and an error message is displayed when trying to validate the extension :
- In the stderr.log fil of the ~SAPBI\tomcat\logs folder, you can find the error :

javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target  at sun.security.ssl.Alert.createSSLException(Alert.java:131)  at sun.security.ssl.TransportContext.fatal(TransportContext.java:377)  at sun.security.ssl.TransportContext.fatal(TransportContext.java:320)  at sun.security.ssl.TransportContext.fatal(TransportContext.java:315) …  at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)  at java.lang.Thread.run(Thread.java:838) Caused by: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target  at sun.security.validator.PKIXValidator.doBuild(PKIXValidator.java:439)  at sun.security.validator.PKIXValidator.engineValidate(PKIXValidator.java:306)  at sun.security.validator.Validator.validate(Validator.java:271)  at sun.security.ssl.X509TrustManagerImpl.validate(X509TrustManagerImpl.java:312)  at sun.security.ssl.X509TrustManagerImpl.checkTrusted(X509TrustManagerImpl.java:221)  at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:128)  at sun.security.ssl.CertificateMessage$T12CertificateConsumer.checkServerCerts(CertificateMessage.java:636)  ... 93 more Caused by: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target  at sun.security.provider.certpath.SunCertPathBuilder.build(SunCertPathBuilder.java:146)  at sun.security.provider.certpath.SunCertPathBuilder.engineBuild(SunCertPathBuilder.java:127)  at java.security.cert.CertPathBuilder.build(CertPathBuilder.java:280)  at sun.security.validator.PKIXValidator.doBuild(PKIXValidator.java:434)

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.3 SP3+
- N4V 2024.1.0+

#### **Resolution**

If the Tomcat is configured with HTTPS, then you may need to add the certificate of the server (SAPBI URL) to the certificate's store of the SAP BI platform.

See the [https://www.need4viz.com/support/kb/faq.php?id=130](https://www.need4viz.com/support/kb/faq.php?id=130) article first.

To achieve that, run the following steps on all SAPBI servers of your deployment/cluster :

- Backup the cacerts file : ~SAPBI\SAP BusinessObjects Enterprise XI 4.0\win64_x64\sapjvm\jre\lib\security\cacerts (BI2025 : ~SAPBI\SAP BusinessObjects Enterprise XI 4.0\win64_x64\sapjvm\lib\security\cacerts)
- Retrieve your server certificate (including the root & intermediary certificates, generally used to configure the HTTPS configuration of Tomcat to access the SAPBI Launchpad) : for instance my_certificate.pem
- Open a command as administrator and goto the folder ~SAPBI\SAP BusinessObjects Enterprise XI 4.0\win64_x64\sapjvm\bin
- Run the command **keytool -importcert -keystore ..\jre\lib\security\cacerts -file your_filename -alias your_alias** (BI2025 : **keytool -importcert -keystore ..\lib\security\cacerts -file your_filename -alias your_alias**). You can name the alias as you want, the **default password** of the cacerts store is "**changeit**"
- Restart the SIA and the Tomcat
- After that, you should be able to add the N4V extension in the CMC

keytool require a .pem format certificat. In case you have a .pfx or something else, you can use openssl tool to convert your certificat to a valid .pem file.

- Install openssl on your server
- Extract the certificate included in the .pfx : **openssl pkcs12 -in mycertificat.pfx -clcerts -nokeys -out cert.pem**
- Extract the ca included in the .pfx : **openssl pkcs12 -in mycertificat.pfx -cacerts -nokeys -out ca.pem**
- concatenate both files : `copy cert.pem + ca.pem fullchain.pem`

The following error means that the encryption method used in the certificate is too old :

`Error outputting keys and certificates CC250000:error:0308010C:digital envelope routines:inner_evp_generic_fetch:unsupported:crypto\evp\evp_fetch.c:375:Global default library context, Algorithm (RC2-40-CBC : 0), Properties ()`

run the command with **-legacy -provider-path "*the_path_to_file_legacy.dll*"**

for instance : ****openssl pkcs12 -in mycertificat.pfx -cacerts -nokeys -out **ca**.pem********-legacy -provider-path "*C:\Program Files\OpenSSL-Win64\bin*"****

[Full article](https://support.need4viz.com/kb/faq.php?id=97)

### Issue when adding the N4V extension in specific Tomcat configuration

#### Symptom

- You want to activate the N4V Webi extensions provided by Need4Viz to enhance the Webi capabilities but an error message is displayed when trying to validate the extension :

- In the stderr.log fil of the ~SAPBI\tomcat\logs folder, you can find the error :

javax.net.ssl|ALL|25|https-openssl-nio-443-exec-4|2026-07-16 13:05:10.012 CEST|SSLSessionImpl.java:1192|Invalidated session: Session(1784199909983|SSL_NULL_WITH_NULL_NULL) javax.net.ssl|DEBUG|25|https-openssl-nio-443-exec-4|2026-07-16 13:05:10.012 CEST|SSLSocketImpl.java:1759|close the underlying socket javax.net.ssl|DEBUG|25|https-openssl-nio-443-exec-4|2026-07-16 13:05:10.012 CEST|SSLSocketImpl.java:1785|close the SSL connection (passive) javax.net.ssl.SSLHandshakeException: Received fatal alert: handshake_failure  at java.base/sun.security.ssl.Alert.createSSLException(Alert.java:131)  at java.base/sun.security.ssl.Alert.createSSLException(Alert.java:117)  at java.base/sun.security.ssl.TransportContext.fatal(TransportContext.java:370)  at java.base/sun.security.ssl.Alert$AlertConsumer.consume(Alert.java:293)  at java.base/sun.security.ssl.TransportContext.dispatch(TransportContext.java:209)  at java.base/sun.security.ssl.SSLTransport.decode(SSLTransport.java:172)  at java.base/sun.security.ssl.SSLSocketImpl.decode(SSLSocketImpl.java:1510)  at java.base/sun.security.ssl.SSLSocketImpl.readHandshakeRecord(SSLSocketImpl.java:1425)  at java.base/sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:455)  at java.base/sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:426)  at java.base/sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:589)  at java.base/sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:187)  at java.base/sun.net.www.protocol.https.HttpsURLConnectionImpl.connect(HttpsURLConnectionImpl.java:142)  at com.businessobjects.adv_ivcdzview.ExtensionHelper.sendRequest(Unknown Source)  at com.businessobjects.adv_ivcdzview.ExtensionHelper.loadExternalExtensionDeclarationForCheck(Unknown Source)  at org.apache.jsp.jsp.WebIntelligence_005fCustomization.checkExternalExtension_jsp._jspService(checkExternalExtension_jsp.java:203)

...

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.3, BI2025
- N4V 2024.1.0+

#### **Resolution**

The Tomcat is configured with HTTPS and a liste of sslEnabledProtocols and/or ciphers are explicitely defined (server.xml file in tomcat/conf foler) :

but those values don't match the autorized values defined in the SAP JVM settings of the java.security file (in SAP BusinessObjects\SAP BusinessObjects Enterprise XI 4.0\win64_x64\sapjvm\conf\security folder - BI2025).

For instance, in the java.security file, the TLSv1 and TLSv1.1 are disabled :

To be sure the values of protocols/ciphers math between Tomcat and the SAPJVM, you can configure the connector as follow (use only TLS1.2 & TLS1.3, do not specify any cipher, Tomcat will use the one autorized by the SAP JVM) :

Once the server.xml file is updated :

- Restart the Tomcat
- Declare the N4V extensions in the CMC
- Clean the cache of your browser
- Open Webi and display the N4V panels

[Full article](https://support.need4viz.com/kb/faq.php?id=128)

### Tomcat HTTPS: fixing the "PKIX path building failed" error

#### Tomcat HTTPS: fixing the "PKIX path building failed" error (ex. DigiCert / GeoTrust / wildcard certificate)

7 oct. 2026 · @NEED4VIZ

#### Symptom

Tomcat writes an `SSLHandshakeException` to its stderr, with the root cause `PKIX path building failed: unable to find valid certification path to requested target`. It appears when Tomcat's JVM opens an HTTPS connection to a server (often the same server, through its public name) whose certificate is a wildcard issued by a DigiCert authority.

```
javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException:
  PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException:
  unable to find valid certification path to requested target
```

**In short:** the JVM knows the root (DigiCert Global Root G2), but the server does not send the intermediate certificate (GeoTrust TLS RSA CA G1). The lasting fix is to make Tomcat send the complete chain, not to edit the `cacerts` file.

#### Why does this error occur?

A certificate is accepted only if the JVM can follow the chain of signatures up to a root it trusts. The chain has three links:

- Link | Example here | Where it must be
- Root | DigiCert Global Root G2 | In the JVM's `cacerts` (shipped by default)
- Intermediate | GeoTrust TLS RSA CA G1 | Sent by the server during the connection
- Leaf certificate | Your wildcard | Sent by the server

The `cacerts` file is the JVM's store of trusted roots, and it already contains the root. The problem is that the PFX used by the Tomcat connector holds only the wildcard. The server therefore does not send the intermediate, the JVM cannot link the wildcard to the root, and the connection is rejected.

**Why not import the wildcard into `cacerts`?** It works (the JVM then trusts the wildcard directly), but the wildcard is renewed every 6 months: the operation must be repeated each time, and forgetting it causes an outage. Moreover, the maximum validity of public certificates keeps shrinking (200 days since March 2026, then 100 and 47 days according to the CA/Browser Forum schedule, to be confirmed), so the manual step would become ever more frequent.

**Why fix it on the server side?** A properly configured server always sends the full chain (leaf + intermediate). Every client benefits, not just Java, and renewing the wildcard never again touches `cacerts`.

#### Diagnosis: which chain does the server send?

From a workstation or the server itself, display the certificates sent by the connector (replace `myserver` and the port):

```
openssl s_client -connect myserver:8443 -servername myserver -showcerts < NUL
```

On Linux, replace `< NUL` with `. On Windows, 'openssl' is available with Git for Windows, for example.`

In the `Certificate chain` section:

- Only `0 s:` (your wildcard): the chain is incomplete, which is the cause of the error.
- `0 s:` (wildcard) **and** `1 s:` (GeoTrust TLS RSA CA G1): the chain is complete and the error comes from elsewhere (another server, another certificate, the server clock, a proxy intercepting TLS).

#### Recommended fix: rebuild the PFX with the full chain

The Tomcat connector sends whatever its PFX file contains. There is therefore **nothing to change in `server.xml`**: you only need a PFX that holds the private key, the wildcard and the intermediate. The existing connector stays as is:

1. **Back up the current PFX.** `copy C:\SAPBI\SSL\my_certificat.pfx C:\SAPBI\SSL\my_certificat.pfx.bak`
2. **Get the GeoTrust TLS RSA CA G1 intermediate** in PEM format: either from the bundle DigiCert supplied with the wildcard, or from DigiCert's certificate page ("Intermediate" section). If it is in DER (binary) format, convert it:`openssl x509 -inform der -in GeoTrustTLSRSACAG1.crt -out intermediate.pem`
3. **Extract the private key and the wildcard from the old PFX.** `openssl pkcs12 -in C:\SAPBI\SSL\my_certificat.pfx -nocerts -nodes -out key.pem openssl pkcs12 -in C:\SAPBI\SSL\my_certificat.pfx -clcerts -nokeys -out leaf.pem`
4. **Rebuild a PFX that includes the chain.** Keep the same password so `keystorePass` stays untouched. Do not add the root: the client already knows it.`openssl pkcs12 -export -inkey key.pem -in leaf.pem -certfile intermediate.pem -name tomcat -out C:\SAPBI\SSL\my_certificat_chain.pfx`
5. **Check the contents.** The output must show `Certificate chain length: 2`.`keytool -list -v -keystore C:\SAPBI\SSL\my_certificat_chain.pfx -storetype PKCS12`
6. **Plug in the new file**: rename it to `my_certificat.pfx`, or change `keystoreFile` (and `keystorePass` if the password changed), then restart Tomcat.
7. **Verify** with the `openssl s_client` command from the diagnosis: both certificates (`0 s:` and `1 s:`) must appear and the PKIX error must be gone, without adding anything to `cacerts`.
8. **Clean up**: delete `key.pem` and `leaf.pem`, which hold the private key in clear text.

If OpenSSL 3.x produces a PFX that an older JVM cannot read, add `-legacy` to the `openssl pkcs12 -export` command.

#### Alternative solutions

- Solution | Principle | Limits
- Import the intermediate into `cacerts` | The JVM then knows GeoTrust TLS RSA CA G1 and can link the wildcard to the root | Fixes only that JVM; must be repeated on every client JVM and after any JVM update that replaces `cacerts`; becomes obsolete if the issuing authority changes
- Let the JVM download the intermediate (AIA extension) | JVM option `-Dcom.sun.security.enableAIAcaIssuers=true` (enabled by default on recent JDKs) | Requires outbound HTTP access from the server to `cacerts.digicert.com` (proxy, firewall); less reliable
- Import the wildcard into `cacerts` | The JVM trusts the certificate directly | Must be redone at every renewal (every 6 months): not recommended

Command to import the intermediate if you choose this route (back up `cacerts` first, check the fingerprint and expiry date of the downloaded file, then restart Tomcat):

```
keytool -importcert -trustcacerts -alias geotrust-tls-rsa-ca-g1 -file GeoTrustTLSRSACAG1.crt -keystore \cacerts -storepass changeit
```

Use the `keytool` of the JVM that runs Tomcat, not one from another JVM on the server.

#### Renewals and frequently asked questions

**At each wildcard renewal**: redo only steps 3 to 6 of the recommended fix with the new key and certificate, reusing the same `intermediate.pem`. `cacerts` is never modified again. If DigiCert has the new wildcard issued by a different intermediate, the certificate delivery names it: download that new intermediate instead.

**Is the "Nov 23, 2017" date shown by `keytool -list` an expiry date?** No, it is the date the entry was added to the keystore. The real validity is shown by `keytool -list -v` (the `Valid from … until …` line).

**Should the `digicertglobalrootg2` entry in `cacerts` be updated?** No: the DigiCert Global Root G2 root is valid until 2038. To refresh all roots at once, update the JVM (SAPJVM / JDK patch) rather than editing `cacerts` entry by entry.

**The error persists after changing the PFX.** Check that Tomcat was restarted, that `keystoreFile` points to the new file, that `openssl s_client` shows two certificates, and that the JVM producing the error is the one running this Tomcat.

**Security.** The wildcard's private key must never stay in clear text: delete the temporary `.pem` files and restrict access to the PFX and its backup.

[Full article](https://support.need4viz.com/kb/faq.php?id=130)

## Issues displaying N4V panels

### Extension doesn't appear in the Webi panel after adding it in the CMC

#### Symptom

- The N4V Webi extensions provided by Need4Viz to enhance the Webi capabilities is correctly loaded in the CMC and affected to a group of users
- The Extensions panel is displayed in Webi but it is empty :

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.3 SP3+
- N4V 2024.1.0+

#### **Resolution**

1/ In some cases, you simply need to refresh the cache of your browser (Shift+F5) to make the N4V extension displayed correctly

2/ Check in the CMC that in the "Applications / Web Intelligence/ Properties"

- "Enable hyperlinks, JavaScript and all HTML elements" is enabled
- "I accept the risk" for the Cross-Site scripting (XSS) is ticked

3/ In other cases, if the extension is hosted on a Tomcat configured with HTTPS, you need to add the certificate of the server (URL SAPBI) into the certifcate's store of the SAP JVM to authorize the loading of entensions files. To achieve this, please follow the instructions in the KB : [https://www.need4viz.com/support/kb/faq.php?id=97](https://www.need4viz.com/support/kb/faq.php?id=97)

[Full article](https://support.need4viz.com/kb/faq.php?id=98)

### Users in CMC customized group don't view all customisations

#### Symptom

- The N4V Webi extensions provided by Need4Viz to enhance the Webi capabilities is correctly loaded in the CMC and affected to a group of users
- Not all extensions are displayed in Webi when the user logged on (or none of them)

#### Reason and Prerequisites

**Environment:**

- SAP BusinessObjects 4.3 SP3+
- N4V 2024.1.0+

#### **Resolution**

In the CMS, customization are affected to each group user.

When a user is a member of many groups affected, only the first group - for which a customization is affected - retrieved by the CMS (sorted by ID) is selected and the according customization are displayed.

To view all the customized groups in the CMS (sorted by ID) :

1/ connect as administrator to the AdminTools webapplication (http(s)://your_domain/AdminTools)

2/ run the following query :

SELECT SI_ID, SI_NAME,SI_DATA FROM CI_INFOOBJECTS,CI_APPOBJECTS,CI_SYSTEMOBJECTS WHERE si_kind='UserGroup' and not SI_DATA.SI_WEBI_CUSTOMIZATION is null

Result is similar to the following one :

In this case, if a user is member of Administrators and test4 groups, only the customization affected for the group administrator will be displayed for the user (even if 4 extensions are affected to the test4 group).

This is because the Administrators group is retrieved firstly by the query (the result is sorted by SI_ID).

3/ To be sure all the extensions are visible for the users, create a specific "generic" group an affect the extensions to that group. Then, add all the groups you need to this "global" group.

[Full article](https://support.need4viz.com/kb/faq.php?id=126)
