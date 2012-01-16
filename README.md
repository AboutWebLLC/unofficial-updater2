# Unofficial Updater 2

## Introduction
Unofficial Updater 2 (UU2) is an outgrowth of the frustration that came from 
trying to manually patch Adobe ColdFusion 8.0.1 with the numerous hot fixes 
and security bulletins that have been published. It is a tool to provide 
an easy way of consistently applying applicable hot fixes and security 
bulletins to Adobe ColdFusion 8.0.1 or 9.0.1.

### Disclaimers
1. Use of Unofficial Updater 2 is **at your own risk**
2. Unofficial Updater 2 can **only be run against** Adobe ColdFusion **8.0.1** or **9.0.1**
 - If you are running **8.0.0** or **9.0.0** you need to apply Update 1 from Adobe first
     - [Adobe ColdFusion 8 Update 1](http://kb2.adobe.com/cps/403/kb403277.html)
     - [Adobe ColdFusion 9 Update 1](http://kb2.adobe.com/cps/849/cpsid_84973.html)
3. Unofficial Updater 2 is **not endorsed by or have any ties** to Adobe
4. Unofficial Updater 2 is **updated** whenever Adobe releases a new (or changes) a hot fix or security bulletin
 - Matrix of published hot fixes and security bulletins
     - [Hot Fix Matrix: ColdFusion 8.0.1](https://github.com/dcepler/unofficial-updater2/blob/master/cf801-hotfix-matrix.pdf?raw=true)
     - [Hot Fix Matrix: ColdFusion 9.0.1](https://github.com/dcepler/unofficial-updater2/blob/master/cf901-hotfix-matrix.pdf?raw=true)    
5. Unofficial Updater 2 will **need to be run again** when it is updated to apply all new (or changed) hot fix or security bulletin from Adobe

## What it does
Unofficial Updater 2 asks specific questions about how Adobe ColdFusion is installed. It 
will then produce backups of any directories it will modify. Finally, it 
will download the applicable hot fixes and security bulletins from Adobe 
and apply them according to the published instructions. It only updates 
files, it will **not modify** any settings such as *jvm.config*, *registry*, etc. A list of files
that Unofficial Updater 2 updates as compared to a clean install of Adobe ColdFusion 8.0.1 or 9.0.1 are listed below:

 - [File Changes: ColdFusion 8.0.1 Standalone](https://raw.github.com/dcepler/unofficial-updater2/master/uu2-cf801-standalone-filechanges.txt) 
 - [File Changes: ColdFusion 8.0.1 Multi-Server JRun4](https://raw.github.com/dcepler/unofficial-updater2/master/uu2-cf801-jrun-filechanges.txt) 
 - [File Changes: ColdFusion 8.0.1 J2EE](https://raw.github.com/dcepler/unofficial-updater2/master/uu2-cf801-j2ee-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.1 Standalone](https://raw.github.com/dcepler/unofficial-updater2/master/uu2-cf901-standalone-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.1 Multi-Server JRun4](https://raw.github.com/dcepler/unofficial-updater2/master/uu2-cf901-jrun-filechanges.txt) 
 - [File Changes: ColdFusion 9.0.1 J2EE](https://raw.github.com/dcepler/unofficial-updater2/master/uu2-cf901-j2ee-filechanges.txt) 
 
If you have modified files in **WEB-INF** and/or **CFIDE/administrator** they could be changed due to files contained in the updates from Adobe.

## How to use
1. [Download](https://github.com/downloads/dcepler/unofficial-updater2/Unofficial-Updater2.jar) the packaged JAR installer
2. Stop the ColdFusion Server/process you are going to update
3. Depending upon your system you might be able to double-click **Unofficial-Updater2.jar** to run it, otherwise it will need to be run from command line
 - **GUI Installer**
      - java -jar Unofficial-Updater2.jar
 - **Text Installer**
      - java -jar Unofficial-Updater2.jar text
4. Walk through the screens putting the appropriate information
 - **Be sure to fill the directory locations correctly**, Unofficial Updater 2 will try to validate they are correct before letting you proceed to the next step
5. Finish updater by pressing **Apply Updates**

Please see the [Wiki](https://github.com/dcepler/unofficial-updater2/wiki/Using-Unofficial-Updater-2) for screenshots and walkthrough.

## Details
At the core, Unofficial Updater 2 is just an [Apache Ant](http://ant.apache.org/) script. Ant was chosen 
since it could provide cross platform support. The ant script was 
wrapped with [Ant Installer](http://antinstaller.sourceforge.net/) to create a GUI and text based interface which
only require Java 1.5+ to be installed.  

### ColdFusion 8.0.1
All hot fixes and security bulletins published as of December 13, 2011 for 
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

### ColdFusion 9.0.1
All hot fixes and security bulletins published as of December 13, 2011 for 
ColdFusion 9.0.1 are applied except if they were superseded by a newer 
patch.

### Session Fixation (APSB11-04)
Please refer to the technote about the Session Fixation issue since 
Unofficial Updater 2 does not modify jvm.config.

 * [APSB11-04 - Security update: Hotfix available for ColdFusion](http://www.adobe.com/support/security/bulletins/apsb11-04.html)
 * [cpsid_89094 - Security Hotfix | ColdFusion 8, 8.0.1, 9, 9.0.1](http://kb2.adobe.com/cps/890/cpsid_89094.html)

Additional information on ColdFusion Session Fixation:

 * [Update on Security Hot-Fix Feb 2011](http://shilpikm.blogspot.com/2011/03/update-on-security-hot-fix-feb-2011.html)
 * [ColdFusion Security Hotfix changes session behaviour](http://cfsimplicity.com/4/coldfusion-security-hotfix-changes-session-behaviour)   

### Backups           
Backups are made one level up of the directory that is modified and are 
in the form **{directory-name}-uu2-{datetime-stamp}.zip**
