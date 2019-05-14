# Build-Cargo-Embedded

Project to check the features of the cargo plugin

## Technology stack
 
 **Back-end stack :**
 - [Liquibase][] - DB migration tool
 - [Spring boot][] - java web framework
 - [Embedded Tomcat][] - servlet container to run project
 - [Gradle][] - build system

## Build configuration
#### Terminal tasks

**BootRun** - build and run project via terminal

    bash ./gradlew bootRun

    gradlew.bat bootRun

**BootWar** - build project for production

    bash ./gradlew bootWar

    gradlew.bat bootWar

**Jar** Command to run binary

    java -jar build/libs/*.war

## Project build tasks

#### Project build properties
 - **cp**   - profile (*rWildfly*, *rTomcat*, *ldTomcat*, *leTomcat*)
 - **ccp**	- container port
 - **crh**	- remote host
 - **cru**	- remote user
 - **crp** 	- remote password
 - **cajp**	- tomcat.ajp.port property *(only for Tomcat profiles)*

#### Project build profiles
You can find it here ./gradle/cargo_*.gradle

 - **Remote Wildfly** rWildfly)
 - **Remote Tomcat** (rTomcat)
 - **Local Tomcat which is Downloaded** (ldTomcat)
 - **Local Tomcat Embedded** from *./embedded* (leTomcat)

### Project terminal build tasks

**Remote Wildfly :**

    bash ./gradlew bootWar cargoRedeployRemote -Pcp=rWildfly
    -Pcrh=localhost -Pccp=9990 -Pcru=admin -Pcrp=admin
    
    gradlew.bat bootWar cargoRedeployRemote -Pcp=rWildfly
    -Pcrh=localhost -Pccp=9990 -Pcru=admin -Pcrp=admin

**Remote Tomcat :**

    bash ./gradlew bootWar cargoRedeployRemote -Pcp=rTomcat
    -Pcrh=localhost -Pccp=8088 -Pcru=admin -Pcrp=admin -Pcajp=9081
    
    gradlew.bat bootWar cargoRedeployRemote -Pcp=rTomcat
    -Pcrh=localhost -Pccp=8088 -Pcru=admin -Pcrp=admin -Pcajp=9081
    
**Local Tomcat, Download from maven :**

    bash ./gradlew bootWar cargoRunLocal -Pcp=ldTomcat
    -Pccp=9080 -Pcajp=9081
    
    gradlew.bat bootWar cargoRunLocal -Pcp=ldTomcat
    -Pccp=9080 -Pcajp=9081

**Local Tomcat Embedded, from project path :**

    bash ./gradlew bootWar cargoRunLocal -Pcp=leTomcat
    -Pccp=9080 -Pcajp=9081

    gradlew.bat bootWar cargoRunLocal -Pcp=leTomcat
    -Pccp=9080 -Pcajp=9081

Required parameter is **-Pcp**, the other parameters have default values ​​as described above.

#### Cargo build task description

 - **Remote**
    * cargoRedeployRemote
    * cargoDeployRemote
    * cargoUndeployRemote

 - **Local**
    * cargoRunLocal         *waits, until tomcat working*
    * cargoConfigureLocal

 - **Local, as container** 
    * cargoStartLocal		*start container, deploy, and do other tasks*
    * cargoRedeployLocal	*redeploy to running container*
    * cargoStopLocal		*stop container*

#### Intellij IDEA configuration

 - **Delegate to gradle** - 
 Press **Ctrl+Alt+S**, go to **Build, Execution, Deployment** -> **Build Tools** -> **Gradle** -> **Runner**
 and enable checkbox **Delegate IDE build/run actions to gradle**

[Spring boot]: https://spring.io/
[Liquibase]: https://www.liquibase.org/
[Embedded Tomcat]: http://tomcat.apache.org/
[Gradle]: https://gradle.org/
