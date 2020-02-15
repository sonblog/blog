---
author: admin
comments: true
date: 2012-05-01 12:19:33+00:00
layout: post
link: https://quachson.com/ejb-enterprise-java-bean/
slug: ejb-enterprise-java-bean
title: EJB - Enterprise Java Bean
wordpress_id: 772
categories:
- EJB
tags:
- EJB
---

### Benefits of Enterprise Beans


For several reasons, enterprise beans simplify the development of large, distributed applications. **First**, because the EJB container provides system-level services to enterprise beans, the bean developer can concentrate on solving business problems. The EJB container--and not the bean developer--is responsible for system-level services such as transaction management and security authorization.

**Second**, because the beans--and not the clients--contain the application's business logic, the client developer can focus on the presentation of the client. The client developer does not have to code the routines that implement business rules or access databases. As a result, the clients are thinner, a benefit that is particularly important for clients that run on small devices.

**Third**, because enterprise beans are portable components, the application assembler can build new applications from existing beans. These applications can run on any compliant J2EE server provided that they use the standard APIs.


###  Types of Enterprise Beans


+ Session Bean ( Stateless, Stateful): Performs a task for a client; implements a web service

+ Entity Bean: Represents a business entity object that exists in persistent storage

+ Message-Driven Bean: Acts as a listener for the Java Message Service API, processing messages asynchronously


## What Is an Entity Bean?


An entity bean represents a business object in a persistent storage mechanism

+ Persistence

+ Shared Access

+ Primary Key

+ Relationships
