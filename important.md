# Unofficial Updater 2

## Introduction
Unofficial Updater 2 (UU2) is an outgrowth of the frustration that came from 
trying to manually patch Adobe ColdFusion 8.0.1 with the numerous hot fixes 
and security bulletins that have been published. It is a tool to provide 
an easy way of consistently applying applicable hot fixes and security 
bulletins to Adobe ColdFusion 8.0.1 and 9.0.x.

### Disclaimers
1. Use of Unofficial Updater 2 is **at your own risk**
 - **Do not** run Unofficial Updater 2 for the first time on a production system
2. Unofficial Updater 2 is **not endorsed by or have any ties** to Adobe
3. ColdFusion Server/process **should not be running** when you use Unofficial Updater 2
4. Unofficial Updater 2 can **only be run against** Adobe ColdFusion **8.0.1**, **9.0.0**, **9.0.1**, or **9.0.2**
 - If you are running **8.0.0** you need to apply Update 1 from Adobe first
     - [Adobe ColdFusion 8 Update 1](http://kb2.adobe.com/cps/403/kb403277.html)
5. Unofficial Updater 2 is **updated** whenever Adobe releases a new (or changes) a hot fix or security bulletin
 - Matrix of published hot fixes and security bulletins
     - [Hot Fix Matrix: ColdFusion 8.0.1](https://github.com/AboutWebLLC/unofficial-updater2/blob/master/cf801-hotfix-matrix.pdf?raw=true)
     - [Hot Fix Matrix: ColdFusion 9.0.0](https://github.com/AboutWebLLC/unofficial-updater2/blob/master/cf900-hotfix-matrix.pdf?raw=true)    
     - [Hot Fix Matrix: ColdFusion 9.0.1](https://github.com/AboutWebLLC/unofficial-updater2/blob/master/cf901-hotfix-matrix.pdf?raw=true)    
     - [Hot Fix Matrix: ColdFusion 9.0.2](https://github.com/AboutWebLLC/unofficial-updater2/blob/master/cf902-hotfix-matrix.pdf?raw=true)    
6. Unofficial Updater 2 will **need to be downloaded and run again** when it is updated to apply all new (or changed) hot fix or security bulletin from Adobe
7. Unofficial Updater 2 works **in most** situations/installs, but if you have something non-standard it might not work
 - Consider contacting a [CF-oriented Troubleshooting Consultant](http://www.cf411.com/cfconsult) to ensure you are properly patched

## What it does
First time you run Unofficial Updater 2, it will download **ALL** hotfixes and
security bulletins from Adobe for both ColdFusion 8.0.1 and 9.0.x. UU2 will 
create **Unofficial-Updater2-with-downloads.jar** which contains the 
downloaded hotfixes and security bulletins. This is done since UU2 
can not directly package the updates and will make it easier to patch 
additional servers without the need of an Internet connection.

Once the downloading is complete, UU2 will asks specific questions about how 
Adobe ColdFusion is installed. It will then produce backups of any directories
it will modify. Finally, it will apply the hotfixes and security bulletins 
according to the published instructions.

UU2 only updates files, it **does not modify** any settings in ColdFusion 
such as *neo-***.xml* or *jvm.config*.

A list of files that Unofficial Updater 2 updates as compared to a clean 
install of Adobe ColdFusion 8.0.1, 9.0.0, 9.0.1, and 9.0.2 are listed below:

 - [File Changes: ColdFusion 8.0.1 Standalone](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf801-standalone-filechanges.txt) 
 - [File Changes: ColdFusion 8.0.1 Multi-Server JRun4](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf801-jrun-filechanges.txt) 
 - [File Changes: ColdFusion 8.0.1 J2EE](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf801-j2ee-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.0 Standalone](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf900-standalone-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.0 Multi-Server JRun4](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf900-jrun-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.0 J2EE](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf900-j2ee-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.1 Standalone](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf901-standalone-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.1 Multi-Server JRun4](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf901-jrun-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.1 J2EE](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf901-j2ee-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.2 Standalone](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf902-standalone-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.2 Multi-Server JRun4](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf902-jrun-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.2 J2EE](https://raw.github.com/AboutWebLLC/unofficial-updater2/master/uu2-cf902-j2ee-filechanges.txt) 
 
If you have modified files in **CFIDE** and/or **WEB-INF** they could be changed due to files contained in the updates from Adobe.

## How to use
1. Download the packaged JAR installer
2. Stop the ColdFusion Server/process you are going to update
3. Depending upon your system you might be able to double-click **Unofficial-Updater2.jar** to run it, otherwise it will need to be run from command line
 - On Windows might need to **Run as Administrator** for GUI or opening command prompt
 - **Installer** (auto-detect GUI or text)
      - `java -jar Unofficial-Updater2.jar`
 - **Force GUI Installer** 
      - `java -jar Unofficial-Updater2.jar swing`
 - **Force Text Installer** 
      - `java -jar Unofficial-Updater2.jar text`
 - **Text Installer run as cfusion user on Linux/UNIX**
      - `su -s /bin/sh "cfusion" -c "java -jar Unofficial-Updater2.jar text"`
 - **Text Installer run as root on Linux/UNIX**
      - `sudo java -jar Unofficial-Updater2.jar text`
 - Once *Unofficial-Updater2-with-downloads.jar* is created, you can use that instead of *Unofficial-Updater2.jar*
4. Walk through the screens putting the appropriate information
 - **Be sure to fill the directory locations correctly**, Unofficial Updater 2 will try to validate they are correct before letting you proceed to the next step
5. Finish updater by pressing **Apply Updates**
6. On OS X/Linux/UNIX verify (and possibly correct) ownership and permission of the files updated

Please see the [Wiki: Using Updater 2](https://github.com/AboutWebLLC/unofficial-updater2/wiki/Using-Unofficial-Updater-2) for screenshots and walkthrough.

## Details
At the core, Unofficial Updater 2 is just an [Apache Ant](http://ant.apache.org/) script. Ant was chosen 
since it could provide cross platform support. The ant script was 
wrapped with [Ant Installer](http://antinstaller.sourceforge.net/) to create a GUI and text based interface which
only require Java 1.5+ to be installed.  

### Backups
Unofficial Updater 2 creates backups of the directories that are modified, but it is **HIGHLY** recommended that you
create your own backups of your ColdFusion installation to restore from in case of a problem. The backups created by UU2
are stored in the directory specified when running UU2 and are named **{directory-name}-uu2-{datetime-stamp}.zip**


### ColdFusion 8.0.1

***APSB12-21 was the LAST security hotfix Adobe released for ColdFusion 8.0.1***

All hot fixes and security bulletins published as of September 11, 2012 for 
ColdFusion 8.0.1 are applied except if they were superseded by a newer 
patch and the following:

 * [kb404026 - Patch for Performance Monitor with ColdFusion 8.0.1](http://kb2.adobe.com/cps/404/kb404026.html)
 * [CVE-2009-1876 - wsconfig.jar update for Apache](http://www.adobe.com/support/security/bulletins/apsb09-12.html)
 * [kb403750 - Using the flexgateway to instantiate multiple instances of CFCs causes objects to be populated as nulls (hf801-71643)](http://kb2.adobe.com/cps/403/kb403750.html)

Both **kb404026** and **CVE-2009-1876** require modifications to be done to the 
system configuration. **kb404026** requires ability to modify the Windows 
registry and **CVE-2009-1876** will modify the connector configuration. 
**kb403750** is not installed since it does not seem to resolve all the issues
and [breaks other things](http://www.mischefamily.com/nathan/index.cfm/2009/10/1/hf80171643-Breaks-Application-Specific-Custom-Tag-Paths).

### ColdFusion 9.0.0
All hot fixes and security bulletins published as of May 14, 2013 for 
ColdFusion 9.0.0 are applied except if they were superseded by a newer 
patch and the following:

 * [cpsid_80719 - ColdFusion 9: Limit access to the Solr collections](http://kb2.adobe.com/cps/807/cpsid_80719.html)
 
**cpsid_80719** requires modifying jetty.xml which is a system configuration change.

### ColdFusion 9.0.1
All hot fixes and security bulletins published as of May 14, 2013 for 
ColdFusion 9.0.1 are applied except if they were superseded by a newer 
patch.

### ColdFusion 9.0.2
All hot fixes and security bulletins published as of May 14, 2013 for 
ColdFusion 9.0.2 are applied except if they were superseded by a newer 
patch.

### Additional Notes
Please refer to the various technotes about changes to configuration options 
since Unofficial Updater 2 only updates files, it **does not modify** any 
settings in ColdFusion such as *neo-***.xml* or *jvm.config*.

#### Cumulative Hotfixes for ColdFusion 9.0.x
 * [Cumulative Hotfix 3 for ColdFusion 9.0.0](http://helpx.adobe.com/coldfusion/kb/cumulative-hotfix-3-coldfusion-900.html)
 * [Cumulative Hotfix 4 for ColdFusion 9.0.1](http://helpx.adobe.com/coldfusion/kb/cumulative-hotfix-4-coldfusion-901.html)
 * [Cumulative Hotfix 1 for ColdFusion 9.0.2](http://helpx.adobe.com/coldfusion/kb/cumulative-hotfix-1-coldfusion-902.html)

#### Security Bulletins
 * [APSB11-04 - Security update: Hotfix available for ColdFusion](http://www.adobe.com/support/security/bulletins/apsb11-04.html)
 * [APSB11-14 - Security update: Hotfix available for ColdFusion](http://www.adobe.com/support/security/bulletins/apsb11-14.html)
 * [APSB11-29 - Security update: Hotfix available for ColdFusion](http://www.adobe.com/support/security/bulletins/apsb11-29.html)
 * [APSB12-06 - Security update: Hotfix available for ColdFusion](http://www.adobe.com/support/security/bulletins/apsb12-06.html)
 * [APSB12-15 - Security update: Hotfix available for ColdFusion 9.0.1 and earlier](http://www.adobe.com/support/security/bulletins/apsb12-15.html)
 * [APSB12-21 - Security update: Hotfix available for ColdFusion 10 and earlier](http://www.adobe.com/support/security/bulletins/apsb12-21.html)
 * [APSB12-26 - Security update: Hotfix available for ColdFusion 10 and earlier](http://www.adobe.com/support/security/bulletins/apsb12-26.html)
 * [APSB13-03 - Security update: Hotfix available for ColdFusion](http://www.adobe.com/support/security/bulletins/apsb13-03.html)
 * [APSB13-10 - Security update: Hotfix available for ColdFusion](http://www.adobe.com/support/security/bulletins/apsb13-10.html)
 * [APSB13-13 - Security update: Hotfix available for ColdFusion](http://www.adobe.com/support/security/bulletins/apsb13-13.html)
 * Additional Information
   * [ColdFusion Security Hotfix APSB12-06 and Big Forms](http://www.cutterscrossing.com/index.cfm/2012/3/27/ColdFusion-Security-Hotfix-and-Big-Forms)

#### Java Support
It is highly recommended to update the underlying JVM that ColdFusion 
uses to the latest available Java 6 (1.6.0) version that is available (Update 45) on ColdFusion 8.0.1 or ColdFusion 9.0.x on Mac OS X.
Java 7 (1.7.0) is supported for ColdFusion 9.0.x on Windows (32 and 64 bit), Linux (32 and 64 bit), and Solaris (64 bit) after the CHFs released in March 2013 are applied. Again updating to the latest Java 7 (Update 21) is highly recommended.

 * [Upgrade Java for ColdFusion](http://helpx.adobe.com/coldfusion/kb/upgrading-java-coldfusion.html)
 * [How to use ColdFusion with an external JVM](http://helpx.adobe.com/coldfusion/kb/change-coldfusion-jvm.html)
 * Additional Information
   * [ColdFusion 9.0.x, Mac OS X, and Java 7](http://blogs.coldfusion.com/post.cfm/new-updates-for-coldfusion-9-9-0-1-9-0-2-and-10-java-7-now-supported#comment-869ED317-0670-4D3C-6CADD847164930CE)
   * [CF911: Have you updated your #ColdFusion JVM to _24 yet? Important security fix for CF 8/9](http://www.carehart.org/blog/client/index.cfm/2011/10/28/CF911-Have-you-updated-your-ColdFusion-JVM-to-24-yet-Important-security-fix-for-CF-89)
   * [Oracle, I download your JDK by eating magic cookies](http://blog.kdecherf.com/2012/04/12/oracle-i-download-your-jdk-by-eating-magic-cookies/)
