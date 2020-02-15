---
author: admin
comments: true
date: 2010-03-10 10:04:48+00:00
layout: post
link: https://quachson.com/hotfixes-wce7/
published: false
slug: hotfixes-wce7
title: Required and recommended fixes for WebSphere Commerce version 7
wordpress_id: 110
categories:
- Lotus Notes
- Portal
- Websphere Application Server
- Websphere Portal
---

Required, recommended, and latest fixes





## WebSphere Application  Server required fixes








<table cellpadding="4" cellspacing="0" border="1" rules="all" >

<tr valign="bottom" >
Fix
Type
Comments
</tr>

<tbody >
<tr >

<td width="15.068493150684931%" valign="top" >WebSphere Application Server version 7.0 Fix Pack 3
</td>

<td width="10.616438356164384%" valign="top" >Fix Pack 3
</td>

<td width="74.31506849315068%" valign="top" >The required level of WebSphere  Application Server is 7.0.0.3, and this version is installed if you use the  WebSphere Application Server DVD image packaged with WebSphere Commerce.


Note: The fixes listed on this page are specific to version 7.0.0.3. It is not recommended that you upgrade your WebSphere Application Server level to 7.0.0.5 or 7.0.0.7 at this time.

</td>
</tr>
<tr >

<td width="15.068493150684931%" valign="top" >[PK96229](http://www-01.ibm.com/support/docview.wss?uid=swg24024591)
</td>

<td width="10.616438356164384%" valign="top" >APAR
</td>

<td width="74.31506849315068%" valign="top" >Addresses an issue where in some  certain conditions, some sensitive information might be logged in ffdc data.
</td>
</tr>
<tr >

<td width="15.068493150684931%" valign="top" >[PK98999](http://www-01.ibm.com/support/docview.wss?uid=swg24024855)
</td>

<td width="10.616438356164384%" valign="top" >APAR
</td>

<td width="74.31506849315068%" valign="top" >Addresses an issue where the  Application Profile service is not closing EAR file resources.
</td>
</tr>
<tr >

<td width="15.068493150684931%" valign="top" >[PK99815](http://www-01.ibm.com/support/docview.wss?uid=swg24024860)
</td>

<td width="10.616438356164384%" valign="top" >APAR
</td>

<td width="74.31506849315068%" valign="top" >Addresses an issue with slow  application deployment resulting from zip file decompression overhead
</td>
</tr>
</tbody>
</table>





Note: If you do  not install WebSphere Application Server from the DVD image packaged with WebSphere Commerce, you must also make sure you have all of the [Fixes included in  the WebSphere Application Server Customized Installation Package](http://localhost:8001/help/topic/com.ibm.commerce.install.doc/refs/rigcipcontents.htm)













## IBM HTTP Server  required fixes








<table cellpadding="4" cellspacing="0" border="1" rules="all" >

<tr valign="bottom" >
Fix
Type
Comments
</tr>

<tbody >
<tr >

<td width="10.884353741496598%" valign="top" >[PK96410](http://www-01.ibm.com/support/docview.wss?uid=swg24024560)
</td>

<td width="11.224489795918368%" valign="top" >APAR
</td>

<td width="77.89115646258503%" valign="top" >Addresses an issue where "proxy:  error reading status line from remote server" appears in the error log intermittently
</td>
</tr>
<tr >

<td width="10.884353741496598%" valign="top" >[PK98225](http://www-01.ibm.com/support/docview.wss?uid=swg24024809)
</td>

<td width="11.224489795918368%" valign="top" >APAR
</td>

<td width="77.89115646258503%" valign="top" >Addresses an issue where some  responses that could have been cached were not being cached, resulting in possible lower performance.
</td>
</tr>
</tbody>
</table>














## DB2 Universal Database required fixes








<table cellpadding="4" cellspacing="0" border="1" rules="all" >

<tr valign="bottom" >
Fix
Type
Comments
</tr>

<tbody >
<tr >

<td width="13.356164383561644%" valign="top" >DB2 Universal Database  Version 9.5.4
</td>

<td width="10.95890410958904%" valign="top" >Fix Pack
</td>

<td width="75.68493150684932%" valign="top" >The required version of DB2 Universal Database is Version 9.5.4, and this version is installed if you use the DB2 DVD image provided by WebSphere Commerce.
</td>
</tr>
</tbody>
</table>














## Lotus Connections  required fix information








<table cellpadding="4" cellspacing="0" border="1" rules="all" >

<tr valign="bottom" >
Fix
Type
Comments
</tr>

<tbody >
<tr >

<td width="10.774410774410773%" valign="top" >[LO43917](http://www-01.ibm.com/support/docview.wss?rs=3265&context=SSYGQH&dc=D400&uid=swg24024415&loc=en_US&cs=UTF-8&lang=en&rss=ct3265lotus)
</td>

<td width="8.754208754208754%" valign="top" >APAR
</td>

<td width="80.47138047138047%" valign="top" >This fix is required for the  Lotus Connections integration with Social Commerce to work.
</td>
</tr>
<tr >

<td width="10.774410774410773%" valign="top" >LO43747
</td>

<td width="8.754208754208754%" valign="top" >APAR
</td>

<td width="80.47138047138047%" rowspan="2" valign="top" >Obtain these two fixes by registering for [Lotus Greenhouse](http://greenhouse.lotus.com/) and then accessing the  following URL:



	
  * [https://greenhouse.lotus.com/wikis/home?lang=en#/wiki/WebSphere%20Commerce%20Support/page/Welcome](https://greenhouse.lotus.com/wikis/home?lang=en#/wiki/WebSphere%20Commerce%20Support/page/Welcome)



</td>
</tr>
<tr >

<td width="10.774410774410773%" valign="top" >LO44560
</td>

<td width="8.754208754208754%" valign="top" >APAR
</td>
</tr>
</tbody>
</table>











# Fixes included in the WebSphere Application Server




# Customized Installation Package










The  WebSphere Application Server DVD packaged with WebSphere Commerce contains a collection of fixes called a  Customized Installation Package (CIP). This page lists all of the fixes contained in this Customized Installation Package. If you do not install WebSphere Application Server using the DVDs or images provided by WebSphere Commerce, you must ensure these fixes are installed.


The CIP is installed by following the steps in [Preparing your systems to  run the WebSphere Commerce installation wizard](http://localhost:8001/help/topic/com.ibm.commerce.install.doc/tasks/tig_custom_prep_for_wizard.htm), or as part of the normal installation steps of a quick or custom installation whenever you install WebSphere Application Server from the DVDs or DVD images provided by WebSphere Commerce.


Note: The  WebSphere Application Server Customized Installation Package also contains  WebSphere Application Server Version 7 Fix pack 3, and upgrades any WebSphere Application Server version 7.0.0.0 installation to version 7.0.0.3 (along with installing the fixes listed on this page).








<table cellpadding="4" cellspacing="0" border="1" rules="all" >

<tr >
APAR
Abstract (Notes)
Where to obtain this fix individually
</tr>

<tbody >
<tr >

<td width="8.27250608272506%" valign="top" >PK77428
</td>

<td width="50.36496350364964%" valign="top" >The getDistributedMap method does not return the base cache, but rather the default cache.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24023384)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK78286
</td>

<td width="50.36496350364964%" valign="top" >Null pointer exception during initialization of Virtual Member Manager's (VMM) dynacache
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24022222)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK78134
</td>

<td width="50.36496350364964%" valign="top" >Security flag is incorrect when Websphere Member Manager (WMM) is migrated to Virtual Member Manager (VMM)
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24022259)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK79324
</td>

<td width="50.36496350364964%" valign="top" >A null pointer exception is thrown when attempting to evaluate the cache name string.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24022179)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK77017
</td>

<td width="50.36496350364964%" valign="top" >The text output from the WebSphere Application Server ANT tasks may fail to display special characters on non-English systems.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24022198)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK78654
</td>

<td width="50.36496350364964%" valign="top" >The message "DualMetaDataLoade E loadWebContainerPorts could not find any http or https ports" might appear in the JVM log.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24022510)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK87356
</td>

<td width="50.36496350364964%" valign="top" >AccessException is caught when Federated User Registries is used in Security Domain
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24023471)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK91232
</td>

<td width="50.36496350364964%" valign="top" >Inter-bus links created between V6.0 and V7.0 buses with dots in their names fail to start with CWSIP0041E errors.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24023886)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK91622
</td>

<td width="50.36496350364964%" valign="top" >EJBDeploy encounters a PackageNotFoundException if the CMP backend database model file (dbm) contains diagram  information
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24023925)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK86137
</td>

<td width="50.36496350364964%" valign="top" >Database User Password is printed in FFDC log in cleartext.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24023927)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK89517
</td>

<td width="50.36496350364964%" valign="top" >NullPointerException occurred when call to runUnderUOW was made with option UOW_TYPE_ACTIVITYSESSION specified.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24023928)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK50921
</td>

<td width="50.36496350364964%" valign="top" >Settings in the ibm-jcajndi.props for Java 2 Connector (J2C) connection factory in an embedded resource adapter are not used.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24023948)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK93786
</td>

<td width="50.36496350364964%" valign="top" >Timestamp attribute of an LDAP server may not be parsed correctly if it contains fractions of a second.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24024129)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK91245
</td>

<td width="50.36496350364964%" valign="top" >When the <required> attribute is set to false a cache id may not be generated.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24024535)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK96517
</td>

<td width="50.36496350364964%" valign="top" >When a request object contains the previewRequest attribute invalidations are not always triggered.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24024536)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK95422
</td>

<td width="50.36496350364964%" valign="top" >Plug-in generator does not produce all url-patterns if the application is based on Servlet Spec 2.5.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?uid=swg24024527)
</td>
</tr>
<tr >

<td width="8.27250608272506%" valign="top" >PK97404
</td>

<td width="50.36496350364964%" valign="top" >SHIP SDK APAR IZ60215 AS WAS IFIXApplying this WebSphere Application Server Java SDK Interim Fix will upgrade your Java V6.0 SDK to SR5 plus IZ60215.
</td>

<td width="41.3625304136253%" valign="top" >[WebSphere Application Server support](http://www-01.ibm.com/support/docview.wss?rs=0&uid=swg24024555)
</td>
</tr>
</tbody>
</table>









![time stamp](http://localhost:8001/help/topic/com.ibm.commerce.base.doc/images/timestamp.gif)Last updated: 03  February 2010
