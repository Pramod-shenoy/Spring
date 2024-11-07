# Day 2 Springboot

##  Exploring Spring framework using XML configuration

Exploring the Spring Framework with XML configuration is a great way to understand how the framework works under the hood. Here’s a quick overview and guide to help you get started:

 ## 1. Setting Up a Basic Spring Project:
Dependencies: Ensure your project has the necessary Spring libraries. If you're using Maven, add:
xml
Copy code
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>YOUR_VERSION</version>
</dependency>
Directory Structure:
src/main/java: Contains your Java source files.
src/main/resources: Place your spring.xml configuration here.

 ## 2. Creating a Simple spring.xml Configuration:
Create a file named spring.xml in src/main/resources:
xml
Copy code
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           https://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="myBean" class="com.example.MyClass">
        <property name="propertyName" value="Hello, Spring!" />
    </bean>

</beans>

## 3. Creating a Bean Class:
Create a class in src/main/java/com/example:
java
Copy code
package com.example;

public class MyClass {
    private String propertyName;

    public void setPropertyName(String propertyName) {
        this.propertyName = propertyName;
    }

    public void display() {
        System.out.println("Property Value: " + propertyName);
    }
}

## 4. Loading the XML Configuration:
In your main method, load the context using ClassPathXmlApplicationContext:
java
Copy code
package com.example;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class App {
    public static void main(String[] args) {
        ApplicationContext context = new ClassPathXmlApplicationContext("spring.xml");
        MyClass myBean = (MyClass) context.getBean("myBean");
        myBean.display();
    }
}

 ## 5. Running the Application:
Compile and run your App class. You should see the output:
mathematica
Copy code
Property Value: Hello, Spring!

 ## 6. Tips for XML Configuration:
Bean Scopes: You can define the scope of beans (singleton, prototype, etc.) using the scope attribute.
xml
Copy code
<bean id="myBean" class="com.example.MyClass" scope="prototype">
    ...
</bean>

 ## Dependency Injection: Inject dependencies using the <property> or <constructor-arg> tags.
Autowiring: Use the autowire attribute to enable autowiring by name, type, or constructor.
Exploring XML configuration helps in understanding the traditional way of configuring Spring beans and learning the fundamentals before moving on to Java-based configuration or annotations.
