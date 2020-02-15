---
author: admin
comments: true
date: 2010-03-10 08:12:49+00:00
layout: post
link: https://quachson.com/how-to-install-wce/
slug: how-to-install-wce
title: How to install WCE ( Websphere Commerce Enterprise) ?
wordpress_id: 92
categories:
- Portal
- Websphere Application Server
- Websphere Portal
tags:
- Portal
---

WCE gồm: Database node, Web Server node, Websphere Commerce node.

Mô hình chung: có 3 loại: one-node, two-node, three-node

**One-node**: Database , Web Server , Websphere Commerce cùng 1 server

**Two-node**:
- Database trên server A.
- Web Server, Websphere Commerce cùng trên server B.

![](http://i538.photobucket.com/albums/ff348/quachson/typ2nd.gif)

**Three-node**:
- Database trên Server A.
- Web Server trên Server B.
- Websphere Commerce trên server C.

![](http://i538.photobucket.com/albums/ff348/quachson/typ3nd.gif)

[WebSphere Commerce software requirements – Windows](http://quachson.wordpress.com/2010/03/10/websphere-commerce-software-requirements-windows/) and can run on AIX (IBM OS), Solaris ( Sun OS) and Linux.

Hardware prerequisites for WebSphere Commerce:
- AIX.
- Linux on xSeries and other Intel based systems.
- Linux on zSeries.
- Linux on IBM Power Systems (formerly System i or System p).
- Solaris.
- **Windows (32 bit operating system):
**

You must ensure that you meet the following minimum hardware requirements before installing WebSphere Commerce:



	
  * You require an Intel Pentium III  733 MHz (1 GHz or higher recommended for a production environment) IBM-compatible personal computer with the following hardware:

	
    * A minimum of 2 GB  of free RAM for the first WebSphere Commerce instance. Each additional WebSphere Commerce instance requires an additional free 1.5 GB of RAM.

	
    * A minimum of 4.5 GB of free disk space on your target  installation drive.

	
    * You also need an additional 900 MB temporary disk space  in the location defined by the Windows %tmp% environment variable.

	
    * If your machine is formatted with FAT 16 or FAT 32  partitioning and the partition is over 1.024 GB, you will need twice as much free disk space.

	
    * If your machine is formatted with FAT 16 or FAT 32  partitioning and the partition is over 2.049 GB, you will need three times as much free disk space.

	
    * The installation wizard will check for adequate free disk  space and will warn you if there is not enough space.




	
  * A DVD-ROM drive.

	
  * A graphics-capable monitor with a color depth of at least  256 colors.

	
  * A mouse or other pointing device. (optional)

	
  * A local area network (LAN) adapter that is supported by  the TCP/IP protocol.


-** Windows (64 bit operating system): **

You must ensure that you meet the following minimum hardware requirements before installing WebSphere Commerce:



	
  * A 64–bit Intel Pentium  processor-based IBM-compatible personal computer with the following hardware:

	
    * A  minimum of 2 GB of free RAM for the first WebSphere Commerce instance. Each additional WebSphere Commerce instance requires an additional free 1.5 GB of RAM.

	
    * A minimum of 4.5 GB of free disk space on your target  installation drive.

	
    * You also need an additional 900 MB temporary disk space  in the location defined by the Windows %tmp% environment variable.

	
    * If your machine is formatted with FAT 16 or FAT 32  partitioning and the partition is over 1.024 GB, you will need twice as much free disk space.

	
    * If your machine is formatted with FAT 16 or FAT 32  partitioning and the partition is over 2.049 GB, you will need three times as much free disk space.

	
    * The installation wizard will check for adequate free disk  space and will warn you if there is not enough space.




	
  * A DVD-ROM drive.

	
  * A graphics-capable monitor with a color depth of at least  256 colors.

	
  * A mouse or other pointing device. (optional)

	
  * A local area network (LAN) adapter that is supported by  the TCP/IP protocol.


_**Notes:**_



	
  1. WebSphere Commerce, _Express Edition_ is only supported on the _Windows_ and _Linux_ operating systems.

	
  2. For all operating systems, ensure your **system clock** is set accurately and consistently for all server tiers (Web, application, and database).

	
  3. Update the latest service packs (SP).

	
  4. Ensure that you **disable any virus** scanning software active on the system. Virus scanning software often interferes with the installation by causing problems when hanging DVDs during the installation. You can **re-enable the virus scanning software immediately** after completing the installation.

	
  5. The paging file size should be double the size of the RAM. For example, 512 MB RAM should have a 1024 MB paging file. The paging file size is adjusted in the Virtual memory dialog box.


To access the Virtual memory dialog box:

	
  1. Select   Start  > Control Panel > System.

	
  2. In System Properties, select the  Advanced  tab.

	
  3. Click  Settings in the  Performance section.

	
  4. Under Virtual memory, click Change.

	
  5. In Performance Options, select the  Advanced tab.




## 




## Networking


**Windows 2003 and 2008:
**



	
  * The system must have a resolvable fully qualified host name. The fully qualified host name is the host name combined with the domain name.


For example, if the host name is system1 and the  domain is mydomain.com, the fully qualified host name is system1.mydomain.com. Issuing the following command from a command prompt session should return the IP address of the system:

    
    nslookup fully_qualified_host_name


The result should be a reply with the correct IP address of the system.


	
  * Ensure that the system is DNS enabled so that there is a  host name and domain present. Pure IP address environments are not supported by WebSphere Commerce.

	
  * The IP address on the system must resolve to a host name (including a domain). To determine if the IP address is mapped to a fully qualified host name, start a command prompt session and issue the following command:

    
    nslookup IP_address


The result should be a reply with the correct fully qualified host name of the system.

	
  * Ensure that all nodes in your configuration can be  reached from other computers in the network by pinging the fully qualified host name of each node in the configuration.

	
  * Ensure that you will have no port conflicts in your planned configuration. For a list of port numbers used by a default installation of WebSphere Commerce, see [Default  port numbers](http://quachson.wordpress.com/2010/03/10/default-port-of-wce/)

	
  * Ensure that the DNS suffix has been set on each node in your planned WebSphere Commerce configuration. To set the DNS suffix:

	
    1. Select Start > Control Panel > System.

	
    2. Select the Computer Name tab and click Change.

	
    3. In the Computer Name Changes  dialog box, click More.

	
    4. Enter the DNS suffix in the Primary DNS suffix of this computer field and click OK.

	
    5. In the Computer Name Changes dialog box, click OK.

	
    6. Click OK to exit System Properties.

	
    7. Reboot the machine for the change to take effect.





