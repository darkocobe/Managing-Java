# Manage Java Browser Settings

Oracle's Java SE includes a browser plug-in which is often a target for hacker exploits. Java 7 update 10 and later supports security options to 1) allow or disallow the plug-in for Java to run applets in the web browser and 2) security levels for the plug-in if browser applets are permitted to run at all.

The Configure-JavaBrowserPlugIn.ps1 PowerShell script can be used to manage these settings on local or remote computers using Group Policy startup scripts or PowerShell remoting. 

This script will create or overwrite the system-wide Java configuration files named '[deployment.config](https://docs.oracle.com/javase/7/docs/technotes/guides/jweb/index.html)' and '[deployment.properties](https://docs.oracle.com/javase/7/docs/technotes/guides/deployment/deployment-guide/properties.html)' in C:\Windows\Sun\Java\Deployment in order to enable or disable Java browser plug-in support for all users.

The script defaults to disabling the Java browser plug-in and to set the Java browser security level to "HIGH", but note that this does not disable standalone Java applications, it only affects the browser. Java plug-in security options are set using various command-line parameters to the script.

To see all of the script's options, open PowerShell and run:

```powershell
get-help -full .Configure-JavaBrowserPlugIn.ps1
```

## Requirements
Computer must have PowerShell 2.0 or later installed with an execution policy which allows scripts to run.

Supported browsers include at least Microsoft Internet Explorer, Google Chrome, and Mozilla Firefox. Changes take effect after closing and reopening the browser.

Script must be run with local Administrators or System privileges, such as with a Group Policy assigned startup script or through PowerShell remoting. The changes made will affect all users who log on locally at the computer.

Note that the script does run Java's ssvagent.exe tool, just like when using the Java Control Panel, but Oracle could change this binary or its command-line switches at any time, hence, the script can be brittle to new updates. Test the script first.

## Legal 
The script is free and in the public domain, you may use it for any purpose whatsoever without restriction. However, that being said...

THIS SCRIPT IS PROVIDED "AS IS" WITH NO WARRANTIES OR GUARANTEES OF ANY KIND, INCLUDING BUT NOT LIMITED TO MERCHANTABILITY AND/OR FITNESS FOR A PARTICULAR PURPOSE. ALL RISKS OF DAMAGE REMAINS WITH THE USER, EVEN IF THE AUTHOR, SUPPLIER OR DISTRIBUTOR HAS BEEN ADVISED OF THE POSSIBILITY OF ANY SUCH DAMAGE. IF YOUR STATE DOES NOT PERMIT THE COMPLETE LIMITATION OF LIABILITY, THEN DO NOT DOWNLOAD OR USE THE SCRIPT. NO TECHNICAL SUPPORT WILL BE PROVIDED.

Java is a product and trademark of Oracle or Sun Microsystems (or whatever).

## Update History
* 5.Jun.2013: First posted to SANS.
* 1.Jun.2017: Moved to GitHub.
