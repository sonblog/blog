---
author: admin
comments: true
date: 2010-06-19 15:56:18+00:00
template: "post"
link: https://quachson.com/hello-portlet-with-myeclipse-over-6-5/
slug: hello-portlet-with-myeclipse-over-6-5
title: Hello Portlet with MyEclipse over 6.5
wordpress_id: 289
categories:
- Portal
- Portlet
tags:
- Portal
- portlet
---

## 1. 							Introduction


This document presents an overview of JSR 168 Portlet development 							features available in MyEclipse 6.5.

To get a better feel for MyEclipse and learning more about it, 							please check out our product 							[Documentation](http://www.myeclipseide.com/ContentExpress-display-ceid-67.html) for more 							material.


[top](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/#top)

  
  





##  2. Adding Portlet Support to Web Projects


In order to create a Portlet project, first it requires you start 							wiith an existing MyEclipse Web Project.  Then you can add 							JSR 168 Portlet Capabilities to it to give it Portlet 							support.  The Portlet Support includes configured 							_web.xml_ (for Portal engines that have this requirement), 							generated 							_portlet.xml_, and all necessary JSR 168 runtime 							libraries.

![](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/images/add_caps.gif)
**Figure 2.1.1: Add Portlet Capabilities to Web 								Project**

The Add Portal Capabilities wizard allows selection of the 							specific Portal engine to support:

![](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/images/portal_caps_wizard.gif)
**Figure 2.1.2: Portal Capabilities Wizard**

Once the Portal Capabilities wizard completes, the Web Project 							will be configured with JSR 168 runtime libraries, 							_web.xml_ will be configured with necessary configuration, 							and a new 							_portlet.xml_ file will have been added to the project as 							shown in Figure 2.1.3.

![](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/images/portlet_project_contents_annot.gif)
** Figure 2.1.3: Initial Portlet Project Contents**


[top](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/#top)

</td>
  



##  3. Portlet Wizard


MyEclipse provides wizards for JSR 168-compliant Portlet 							creation.  This wizards can be invoked from the File > 							New > Other... > MyEclipse > Web category as shown in 							Figure 3.1.

![](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/images/portlet_wizard_list.gif)
**Figure 3.1 New MyEclipse Portlet Wizard**

This wizard will create the Portlet class and other required (or 							optional) resources in addition to registering the new portlet in 							the 							_portlet.xml_ descriptor. First page of the wizard 							configures the Portlet class and allows the user to select from 							the list of predefined Portlet templates:

![](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/images/portlet_wizard_1st_page.gif)
**Figure 3.2 First page of the Portlet wizard**

MyEclipse 6.5 provides following Portlet templates:



	
  1. _Portlet with JSPs_ - this Portlet delegates all requests 								to JSPs corresponding to portlet mode. This allows clearer 								separation of the application logic from the UI and to leverage 								JSP support provided by MyEclipse IDE.

	
  2. _Simple Portlet_ - this template will create simple Portlet 								class with method stubs for the request handling methods.


Second page of the wizard allows further customize your new 						portlet and to specify template-specific portlet settings:

![](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/images/portlet_wizard_2nd_page.gif)
**Figure 3.3 Second page of the Portlet wizard**


[top](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/#top)

  
  


<td valign="top" >


## 4. Deploying Portlet Application


MyEclipse 6.5 does not current support direct deployment of the 							Portal Web Projects directly to a portal server. The reason for 							this is that each portlet server out there can have varying 							deployment requirements, and at the moment the deployment tool in 							MyEclipse doesn't know how to deploy Portlets to those servers. 							This is something we want to improve in a future release.

To deploy portal application to JSR 168-compatible portal engine 							the project should be exported as deployable WAR file.

![](http://www.myeclipseide.com/documentation/quickstarts/portlet_overview/images/portlet_export_wizard.gif)
**Figure 4.1 WAR export wizard**

The resulting WAR file should be deployed to the portal server 							using the server-specific deployment tools or follow the specific 							deployment instructions provided by the portlet server.  
  

How to know deploy portlet, here: [ How to deploy portlet ](http://quachson.wordpress.com/2010/03/02/portlet-tutorial-deploying-your-first-portlet-to-openportal-portlet-container-2-0/)
