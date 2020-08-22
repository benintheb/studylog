# Spring Framework

[course](https://inf.run/sWCA) from inflearn.

---

Spring Framework provides DI, AOP, MVC, JDBC as its core functions. These are not new functions that were made with the Spring Framework, but are existing ways of structural programming. 

---

## Spring Framework Modules

The functions of the Spring Framework are all modularizated, to be added to a project when needed.

- spring-core: Provides the core of the Spring Framework- DI(Dependency Injection), and IoC(Inversion of Control)
- spring-aop: Provides AOP(Aspect Oriented Programming)
- spring-jdbc: A tool to interact with the database
- spring-tx: A transaction related tool
- spring-webmvc: Provides the MVC tool. Model, View, Controller

These are just some of the modules that the framework provides. These modules can be added to a project through a XML file.

---

## Spring Container

When modules are declared in a XML file, object related to the modules are created and stored in the container. These objects are called beans in the Spring Framework, and they are used later for development.

