---
author: client
comments: false
date: 2017-09-26 15:51:40+00:00
layout: post
link: https://quachson.com/tips-work-java-restful/
slug: tips-work-java-restful
title: Some tips work with Java restful.
wordpress_id: 1401
categories:
- Java
tags:
- Java
- RESTful
---

Nowadays most people are acquired with microservices restful. Now let's take some time to explore what REST means and what a REST API is. REST stands for "REpresentational State Transfer".

What are the basic features of a RESTful architecture:



 	
  1. Stateless: Client data is not stored on the server between interactions and the session is stored client-side (typically in session storage).

 	
  2. Client<->Server: There is a separation of concerns between the frontend (client) and the backend (server). They operate independently of each other and both are replaceable.

 	
  3. Cache: Data from the server can be cached on the client, which can improve performance speed.


Here are some websites very useful.

 	
  * http://www.mocky.io : mock json online

 	
  * http://www.jsonschema2pojo.org/ : convert json string to polo object (press Preview)


![](https://quachson.com/wp-content/uploads/jsonschema2pojo-300x287.png)



 	
  * https://codebeautify.org/jsonviewer : json formatter

 	
  * https://www.base64decode.org/ : Decode from Base64 format

 	
  * https://www.freeformatter.com/json-escape.html : Convert string to String in Java and otherwise.

 	
  * What http client in java do you prefer to use ?

 	
    * Java core: of course HttpClient (Apache) but the project on which I'm working is Spring MVC, thus I prefer to use RestTemplate.




 	
  * What a library do you use to parse son ?

 	
    * I'm using GSON because my project is a micro services that deals with lots of small JSON requests, then GSON is the library of interest. If you have an environment that deals often with big JSON files, then Jackson is suitable library. GSON struggles the most with big files.




 	
  * What tools do you use to test RESTful APIs ?

 	
    * Postman, SOAP UI.




 	
  * If your service must have call other Rest service, you should have

 	
    * Handle in circumstance that its offline

 	
    * Mock service or mock json

 	
    * Unit test for both failed or successful cases because you don't know when the Rest service updates/changes API or json structure.




 	
  * Name jar/war package: please remove SNAPSHOT.

 	
    * ex: xxx-common-1.0.0-SNAPSHOT.war

 	
    * It's too long for you when call API: https://xxx-common-1.0.0-SNAPSHOT/abc/xyz




 	
  * RestTemplate is thread-safe, thus we can use singleton.

 	
  * Những thư viện maven hay dùng

 	
    * org.projectlombok.lombok: dùng thay thế cho getter/setter

 	
    * org.modelmapper.modelmapper: dùng để copy properties giữa entity và DTO

 	
    * io.jsonwebtoken.jjwt: jwt for java




 	
  * @Valid: validate request parameter in controller

 	
    * @NotNull(message= "First name can not be null")

 	
    * @Size(min=2, message="First name must not be less than 2 characters")

 	
    * @Email




 	
  * 

