---
author: quachson
comments: true
date: 2016-05-26 07:35:57+00:00
template: "post"
link: https://quachson.com/spring-document-notes/
published: false
slug: spring-document-notes
title: Spring document notes
wordpress_id: 1257
categories:
- Spring
tags:
- Spring
---

- PropertyPlaceholderConfigurer 
	-  for @Autowired @Qualifier("id"), @Resource(name="id"), @Injection
	- @Primary: có 2 bean cùng dc declare, bean có primary="true" sẽ dc @Autowire
	- @PostConstruct, init in xml and @PreDestroy, destroy in xml
	- profile in XML and many ways to active profile
		+ http://www.baeldung.com/spring-profiles
		+ in web.xml, caterina trong tomcat
		+ override onStartup() of WebApplicationInitializer interface
		+ java -Dspring.profiles.active
	- ResourceBundleMessageSource implement interface MessageSource
  - ApplicationEvent, ApplicationListener, ApplicationEventPublisher
	- Resource interface has: 
    + UrlResource: http://..., ftp://
    + ClassPathResource: classpath:/aa/aa
    + FileSystemResource: file or url
    + ServletContextResource
    + InputStreamResource
    + ByteArrayResource
  - ApplicationContext 
    + ClassPathXmlApplicationContext("conf/appContext.xml");
    + FileSystemXmlApplicationContext("conf/appContext.xml")
  - Validator, DataBinder, PropertyEditor, Errors, ValidationUtils
  - Spring Expression Language (SpEL): 
    + #{  } in XML
  - AOP: Aspect-Oriented Programming
    + Join point: method execute or handle exception    
    + Pointcut: expression or matched any point join
    + Advice: action taken by an aspect at a particular join point. "around," "before" and "after" advice
	- @Test
    @Sql("/test-data.sql")	
  - Transaction Management 
    + Global transactions:
      ++ JTA (Java Transaction API): JNDI
      ++ EJB CMT: (Container Managed Transaction)
    + Local transactions: JDBC connection, cannot work across multiple transactional resources 
        (JDBC connection cannot run within a global JTA transaction)
    + PlatformTransactionManager interface    
    + 
  - DAO
    + JdbcTemplate 
    + 18.7.2 Handling BLOB and CLOB objects
  - 19.3.3 Declarative transaction demarcation   
  - 20. Marshalling XML using O/X Mappers
    + Marshaller:  object --> XML
    + Unmarshaller:  XML --> object
  - 21.3.2 Mapping Requests With @RequestMapping
    + Supported method argument types (search in spring document for references)
    + Parameter: @RequestParam, @PathVariable, @MatrixVariable, @RequestHeader, @RequestBody, @RequestPart (upload files)
        ++ @RequestBody: use with HttpMessageConverters 
          - ByteArrayHttpMessageConverter: converts byte arrays.
          - StringHttpMessageConverter: converts strings.
          - FormHttpMessageConverter: converts form data to/from a MultiValueMap.
          - SourceHttpMessageConverter: converts to/from a javax.xml.transform.Source. 
          
        ++ use for get: @PathVariable @DateTimeFormat(iso=ISO.DATE) Date day 
            http://www.example.com/users/{userId}
            int, long, Date, String, ...
        ++ @Valid AppointmentForm appointment 
        ++ consumes="application/json"  --> content-type of Header
        ++ produces = MediaType.APPLICATION_JSON_UTF8_VALUE --> accept of Header
    + Return: void, String, ModelAndView, Model, View, Object, ModelMap, @ResponseBody, ResponseEntity, Map, HttpEntity (Headers)
  - @ModelAttribute
    + method: run before @RequestMapping
    + argument: 
      @RequestMapping(path = "/owners/{ownerId}/pets/{petId}/edit", method = RequestMethod.POST)
      public String processSubmit(@ModelAttribute Pet pet) { }  
  - Mapping cookie values with the @CookieValue annotation
  - Customizing data binding with @InitBinder
  - Advising controllers with @ControllerAdvice
    http://docs.spring.io/spring-framework/docs/4.2.6.RELEASE/javadoc-api/org/springframework/web/bind/annotation/ControllerAdvice.html
    + All classes in package
    + all classes with annotaion @: @RestController, @Controller
  - 21.4.1 Intercepting requests with a HandlerInterceptor: RequestMappingHandlerAdapter 
  - 21.5.1 Resolving views with the ViewResolver interface
  - 21.9.3 Theme resolvers: define css in properties files and theme name with cookies or session.
  - 21.10 Spring’s multipart (file upload) support
  - 21.11 Handling exceptions
  - 21.16.12 Message Converters (tìm hiểu thêm về MappingJackson2XmlHttpMessageConverter, Jackson2ObjectMapperFactoryBean)
  - 22.5.4 Using Spring’s form tag library
  - 25. WebSocket Support
  - Part VII. Integration
