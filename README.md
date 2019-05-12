# Template

## Technology stack
 
 **Back-end stack :**
 - [Liquibase][] - DB migration tool
 - [Spring boot][] - java web framework
 - [Embedded Tomcat][] - servlet container to run project
 - [Gradle][] - build system

## Build configuration
#### Terminal tasks

**Jar** Command to run binary

    java -jar build/*.war

#### Intellij IDEA configuration

 - **Delegate to gradle** - 
 Press **Ctrl+Alt+S**, go to **Build, Execution, Deployment** -> **Build Tools** -> **Gradle** -> **Runner**
 and enable checkbox **Delegate IDE build/run actions to gradle**

[Spring boot]: https://spring.io/
[Liquibase]: https://www.liquibase.org/
[Embedded Tomcat]: http://tomcat.apache.org/
[Gradle]: https://gradle.org/
