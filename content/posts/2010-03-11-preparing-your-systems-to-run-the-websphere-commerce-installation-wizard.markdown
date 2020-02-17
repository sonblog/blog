---
author: admin
comments: true
date: 2010-03-11 02:24:11+00:00
template: "post"
link: https://quachson.com/preparing-your-systems-to-run-the-websphere-commerce-installation-wizard/
slug: preparing-your-systems-to-run-the-websphere-commerce-installation-wizard
title: Preparing your systems to run the WebSphere Commerce installation wizard
wordpress_id: 115
categories:
- Websphere Application Server
tags:
- IBM Websphere Commerce
---



Before starting the WebSphere Commerce installation wizard, complete the following checklist.


**Procedure**





	
  1. Review the WebSphere Commerce README file. The README file contains information about last-minute changes to the product. Last-minute changes can include additional fixes that must be installed before using WebSphere Commerce.For more information, see [Reviewing the README file](http://localhost:8001/help/topic/com.ibm.commerce.install.doc/tasks/tig_review_readme_custom.htm#review_readme_custom).

	
  2. ![AIX](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngaix.gif)![Linux](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/nglinux.gif)![Solaris](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngsolaris.gif)![Windows](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngwin.gif)If you have removed DB2 Universal Database, WebSphere Application Server, WebSphere Application Server Web server plug-ins, or IBM HTTP Server from your system and you want the WebSphere Commerce installation wizard to install them in the same location where they were installed earlier:

	
    1. Back up any files from the directories you want to keep.

	
    2. Delete the directories. The directories will be recreated during the installation.You must specify a nonexistent directory before you can continue with the WebSphere Commerce installation.




	
  3. ![Windows](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngwin.gif) Ensure that the Windows administration user ID under which the installation is performed has the appropriate user rights. For instructions on granting user rights, refer to [Granting user rights to a Windows user ID](http://localhost:8001/help/topic/com.ibm.commerce.install.doc/tasks/tig_win_grant_user_rights_custom.htm).

	
  4. ![Windows](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngwin.gif) Ensure the Windows administration user ID under which the installation is performed is not the same as the host name of the machine. For example, for a machine with a host name of machine1, the administration user ID under which the installation is performed should not be machine1.

	
  5. ![Windows](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngwin.gif) If you have an antivirus program active, disable it. Antivirus programs interfere with the installation wizard when you change DVDs in the DVD-ROM drive.

	
  6. ![Windows](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngwin.gif) If you have any applications running, stop them.

	
  7. Ensure that any Lotus Notes server, Web servers, Java application servers, and any nonessential Java processes are stopped before installing WebSphere Commerce.

	
  8. Ensure that any other InstallShield MultiPlatform installers have completed or you have exited them before installing WebSphere Commerce.

	
  9. ![Linux](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/nglinux.gif) When installing your database, ensure your firewall configuration is set according to your database product requirements. Specifically, when using Red Hat Enterprise Linux 5, ensure your firewall configuration is not set to SELinux:Enforcing. If it set to SELinux:Enforcing, a problem may be encountered when installing DB2.

	
  10. ![Windows](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngwin.gif) Stop any database servers on the system.

	
  11. If you have a Web server or any other service on your machine that is currently using any of the following ports: 80, 443, 5432, 5433, 8000, 8001, 8002, 8004, 8006, and 8007, stop the Web server.

	
  12. ![Windows](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngwin.gif)If you plan to use IBM HTTP Server as your Web server, do the following:

	
    1. Ensure that the host name of the Web server machine does not contain an underscore ( _ ). IBM HTTP Server does not support machines with an underscore in their host name.

	
    2. Uninstall IIS if you no longer need it or stop the following services, if they exist on your Windows system:

	
      * IIS Admin Service

	
      * World Wide Web Publishing Service

	
      * Simple Mail Transport Protocol (SMTP)


You should also set these services to disabled, rather than manual or automatic so that they do not start when you restart your system. Service settings are changed from the Services panel. To access the Services panel, select Start > Control Panel > Administrative Tools > Services.




	
  13. ![AIX](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngaix.gif)![Solaris](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngsolaris.gif)![Linux](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/nglinux.gif) Create the user IDs and groups required by WebSphere Commerce on any machine on which you plan to install WebSphere Commerce or WebSphere Commerce Payments. For instructions, refer to [Creating required WebSphere Commerce users and groups](http://localhost:8001/help/topic/com.ibm.commerce.install.doc/tasks/tig_create_required_users_custom.htm).

	
  14. ![AIX](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngaix.gif)![Linux](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/nglinux.gif)![Solaris](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngsolaris.gif) Ensure that your operating system does not log your command line inputs.

	
  15. ![Linux](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/nglinux.gif)![WebSphere Commerce Professional](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngpro.gif)![WebSphere Commerce Enterprise](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/ngent.gif) Transfer required installation files from a workstation to the server.

	
  16. Required: If you are using an existing installation of WebSphere Application Server version 7.0.0.3, you must use the WebSphere Application Server DVD provided with WebSphere Commerce to update your WebSphere Application Server with required fixes.To update your existing WebSphere Application Server with the required fixes:

	
    1. Disable any active antivirus software, otherwise the update installer may not be able to update files during the update procedure.

	
    2. On the machine where WebSphere Application Server is installed, navigate to the location of the WebSphere Application Server DVD image.

	
    3. Start a command prompt.

	
    4. Change directories to the disk2WAS directory on the install image.

	
    5. Run the install.exe command.

	
    6. Select your WebSphere Application Server.

	
    7. Select Apply maintenance and add feature.

	
    8. Select your WebSphere Application Server installation directory. Click Next.

	
    9. When the update installation wizard completes, click Finish.






