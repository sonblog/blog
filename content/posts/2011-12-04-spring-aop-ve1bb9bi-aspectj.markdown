---
author: admin
comments: true
date: 2011-12-04 16:19:00+00:00
template: "post"
link: https://quachson.com/spring-aop-v%e1%bb%9bi-aspectj/
slug: spring-aop-v%e1%bb%9bi-aspectj
title: Spring AOP với AspectJ
wordpress_id: 689
categories:
- Java
- Spring
tags:
- AOP
- Java
- Spring
---

Làm thế nào để tích hợp AspectJ annotation với Spring AOP framework.

AspectJ annotations thông thường là:



	
  1. **@Before** – Được thực thi chèn vào trước khi phương thức được gọi

	
  2. **@After** – Được thực thi sau khi phương thức đã kết thúc

	
  3. **@AfterReturning** – **** – Được thực thi sau khi phương thức trả về kết quá

	
  4. **@AfterThrowing** – Được thực thi sau khi phương thức xảy ra exception

	
  5. **@Around** – Run around the method execution, combine all three advices above


xem cấu trúc của project


![](http://quachson.files.wordpress.com/2011/12/aspectj_structure.png)
























Để gọi được aspect phải có có ít nhất 3 thư viện này:

aspectjrt.jar, aspectjweaver.jar và spring-aop.jar.

**2> Spring Bean:**

Interface Customer

[code]

package com.sample.customer;

public interface Customer {

void addCustomer();

String addCustomerReturnValue();

void addCustomerThrowException() throws Exception;

void addCustomerAround(String name);
}

[/code]

class CustomerImpl hiện thực từ interface Customer

[code]
package com.sample.customer.impl;

import com.sample.customer.Customer;

public class CustomerImpl implements Customer {

public void addCustomer(){
System.out.println("addCustomer() is running ");
}

public String addCustomerReturnValue(){
System.out.println("addCustomerReturnValue() is running ");
return "abc";
}

public void addCustomerThrowException() throws Exception {
System.out.println("addCustomerThrowException() is running ");
throw new Exception("Generic Error");
}

public void addCustomerAround(String name){
System.out.println("addCustomerAround() is running, args : " + name);
}
}
[/code]




#### 3. Enable AspectJ



    
    Để bặt chức năng AspectJ, trong XML config file ta thêm “<code><aop:aspectj-autoproxy /></code>“<em>
    File : Spring-Customer.xml</em>
    [code]
    <beans xmlns="http://www.springframework.org/schema/beans"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:aop="http://www.springframework.org/schema/aop"
        xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans-3.0.xsd 
        http://www.springframework.org/schema/aop 
        http://www.springframework.org/schema/aop/spring-aop-3.0.xsd ">
    
        <aop:aspectj-autoproxy />
    
        <bean id="customer" class="com.sample.customer.impl.CustomerImpl"/>
    
        <!-- Aspect -->
        <bean id="logAspect" class="com.sample.aspect.LoggingAspect"/>
    
    </beans>
    [/code]
    
    
    <h4>4. AspectJ @Before</h4>
    
    In below example, the <code>logBefore()</code> method will be executed before the execution of customerBo interface, <code>addCustomer()</code> method.
    
    <div><strong>Note</strong>
     AspectJ “pointcuts” is used to declare which method is going to intercept, and you should refer to this <a href="http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/aop.html#aop-pointcuts" target="_blank">Spring AOP pointcuts guide</a> for full list of supported pointcuts expressions.</div>
    
    <em>File : LoggingAspect.java</em>
    
    <div>
    <div>
    
    
    package com.mkyong.aspect;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Before;
    
    @Aspect
    public class LoggingAspect {
    
    	@Before("execution(* com.mkyong.customer.bo.CustomerBo.addCustomer(..))")
    	public void logBefore(JoinPoint joinPoint) {
    
    		System.out.println("logBefore() is running!");
    		System.out.println("hijacked : " + joinPoint.getSignature().getName());
    		System.out.println("******");
    	}
    
    }








Run it







    
    	CustomerBo customer = (CustomerBo) appContext.getBean("customerBo");
    	customer.addCustomer();








Output







    
    logBefore() is running!
    hijacked : addCustomer
    ******
    addCustomer() is running










#### 5. AspectJ @After


In below example, the `logAfter()` method will be executed after the execution of customerBo interface, `addCustomer()` method.

_File : LoggingAspect.java_







    
    package com.mkyong.aspect;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.After;
    
    @Aspect
    public class LoggingAspect {
    
    	@After("execution(* com.mkyong.customer.bo.CustomerBo.addCustomer(..))")
    	public void logAfter(JoinPoint joinPoint) {
    
    		System.out.println("logAfter() is running!");
    		System.out.println("hijacked : " + joinPoint.getSignature().getName());
    		System.out.println("******");
    
    	}
    
    }








Run it







    
    	CustomerBo customer = (CustomerBo) appContext.getBean("customerBo");
    	customer.addCustomer();








Output







    
    addCustomer() is running 
    logAfter() is running!
    hijacked : addCustomer
    ******










#### 6. AspectJ @AfterReturning


In below example, the `logAfterReturning()` method will be executed after the execution of customerBo interface, `addCustomerReturnValue()` method. In addition, you can intercept the returned value with the “**returning**” attribute.

To intercept returned value, the value of the “returning” attribute (result) need to be same with the method parameter (result).

_File : LoggingAspect.java_







    
    package com.mkyong.aspect;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.AfterReturning;
    
    @Aspect
    public class LoggingAspect {
    
       @AfterReturning(
          pointcut = "execution(* com.mkyong.customer.bo.CustomerBo.addCustomerReturnValue(..))",
          returning= "result")
       public void logAfterReturning(JoinPoint joinPoint, Object result) {
    
    	System.out.println("logAfterReturning() is running!");
    	System.out.println("hijacked : " + joinPoint.getSignature().getName());
    	System.out.println("Method returned value is : " + result);
    	System.out.println("******");
    
       }
    
    }








Run it







    
    	CustomerBo customer = (CustomerBo) appContext.getBean("customerBo");
    	customer.addCustomerReturnValue();








Output







    
    addCustomerReturnValue() is running 
    logAfterReturning() is running!
    hijacked : addCustomerReturnValue
    Method returned value is : abc
    ******










#### 7. AspectJ @AfterReturning


In below example, the `logAfterThrowing()` method will be executed if the customerBo interface, `addCustomerThrowException()` method is throwing an exception.

_File : LoggingAspect.java_







    
    package com.mkyong.aspect;
    
    import org.aspectj.lang.JoinPoint;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.AfterThrowing;
    
    @Aspect
    public class LoggingAspect {
    
       @AfterThrowing(
          pointcut = "execution(* com.mkyong.customer.bo.CustomerBo.addCustomerThrowException(..))",
          throwing= "error")
        public void logAfterThrowing(JoinPoint joinPoint, Throwable error) {
    
    	System.out.println("logAfterThrowing() is running!");
    	System.out.println("hijacked : " + joinPoint.getSignature().getName());
    	System.out.println("Exception : " + error);
    	System.out.println("******");
    
        }
    }








Run it







    
    	CustomerBo customer = (CustomerBo) appContext.getBean("customerBo");
    	customer.addCustomerThrowException();








Output







    
    addCustomerThrowException() is running 
    logAfterThrowing() is running!
    hijacked : addCustomerThrowException
    Exception : java.lang.Exception: Generic Error
    ******
    Exception in thread "main" java.lang.Exception: Generic Error
    	//...










#### 8. AspectJ @Around


In below example, the `logAround()` method will be executed before the customerBo interface, `addCustomerAround()` method, and you have to define the “`joinPoint.proceed();`” to control when should the interceptor return the control to the original `addCustomerAround()` method.

_File : LoggingAspect.java_







    
    package com.mkyong.aspect;
    
    import org.aspectj.lang.ProceedingJoinPoint;
    import org.aspectj.lang.annotation.Aspect;
    import org.aspectj.lang.annotation.Around;
    
    @Aspect
    public class LoggingAspect {
    
       @Around("execution(* com.mkyong.customer.bo.CustomerBo.addCustomerAround(..))")
       public void logAround(ProceedingJoinPoint joinPoint) throws Throwable {
    
    	System.out.println("logAround() is running!");
    	System.out.println("hijacked method : " + joinPoint.getSignature().getName());
    	System.out.println("hijacked arguments : " + Arrays.toString(joinPoint.getArgs()));
    
    	System.out.println("Around before is running!");
    	joinPoint.proceed(); //continue on the intercepted method
    	System.out.println("Around after is running!");
    
    	System.out.println("******");
    
       }
    
    }








Run it







    
    	CustomerBo customer = (CustomerBo) appContext.getBean("customerBo");
    	customer.addCustomerAround("mkyong");








Output







    
    logAround() is running!
    hijacked method : addCustomerAround
    hijacked arguments : [mkyong]
    Around before is running!
    addCustomerAround() is running, args : mkyong
    Around after is running!
    ******










#### Conclusion


It’s always recommended to apply the least power AsjectJ annotation. It’s rather long article about AspectJ in Spring. for further explanations and examples, please visit the reference links below.

Nguồn: http://www.mkyong.com

    
    
    
    
