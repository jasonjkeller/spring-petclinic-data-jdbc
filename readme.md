# Spring PetClinic Sample Application built with Spring Data JDBC

This is a branch of the official [Spring PetClinic](https://github.com/spring-projects/spring-petclinic) application with domain & persistence layer built with [Spring Data JDBC](https://projects.spring.io/spring-data-jdbc/) instead of [Spring Data JPA](https://projects.spring.io/spring-data-jpa/).

Check original project [readme](https://github.com/spring-projects/spring-petclinic/blob/master/readme.md) for introduction the project, how to run, and how to contribute.

## Understanding the Spring Petclinic application with a few diagrams

[See the presentation here](http://fr.slideshare.net/AntoineRey/spring-framework-petclinic-sample-application)

## Interesting Spring Petclinic forks

The Spring Petclinic master branch in the main [spring-projects](https://github.com/spring-projects/spring-petclinic)
GitHub org is the "canonical" implementation, currently based on Spring Boot and Thymeleaf.

This [spring-petclinic-data-jdbc](https://github.com/spring-petclinic/spring-petclinic-data-jdbc) project is one of the [several forks](https://spring-petclinic.github.io/docs/forks.html) 
hosted in a special GitHub org: [spring-petclinic](https://github.com/spring-petclinic).
If you have a special interest in a different technology stack
that could be used to implement the Pet Clinic then please join the community there.

## Running with OpenTracing Java SpecialAgent 

>With [Static Deferred Attach](https://github.com/opentracing-contrib/java-specialagent#223-static-deferred-attach), the application is executed with the -javaagent argument, but the agent initialization is deferred until the application is started. This mode requires 1 command from the command line, and is designed specifically for Spring runtimes that have complex initialization lifecycles. The SpecialAgent relies on the ContextRefreshedEvent to signify that the application is ready, and thus to cue agent initialization. This approach works for all versions of Spring and Spring Boot.

This consists of adding `-Dsa.spring` but it seems to be broken (see [issues/165](https://github.com/opentracing-contrib/java-specialagent/issues/165)). AVOID IF POSSIBLE!!!

### Running in Intellij

Add the following system properties to the application's run configuration in the `VM options`, making sure to add a valid `nr.apiKey`:

```
-javaagent:./opentracing-specialagent-1.4.2-SNAPSHOT.jar -Dsa.tracer=./newrelic-tracer-java-1.0-SNAPSHOT-all.jar -Dsa.log.level=INFO -Dnr.apiKey=XXX -Dnr.serviceName="Spring Petclinic JDBC"
```
