# Demo Camel SFTP with Spring Boot

# To run

Firstly, to open terminal and making sure JAVA_HOME is set to JDK11

Then start sftp server per "Set up sftp server on local windows machine"

finally run below command in terminal

```
mvnw spring-boot:run
```

any files in "c:\run\sftp-share" will be processed and moved into "c:\run\sftp-share\.done"

# Set up sftp server on local windows machine

## to start sftp server Docker container
Steps
- install Docker Desktop (https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- in Docker Desktop (settings|resources|file sharing), please make sure add "c:\run" so it can be recognized by Docker Desktop.
- copy "<camel-sftp repo>\run" to "c:\run"
- then run "c:\run\start-docker.bat"

## to verify sftp connection through WinSCP
Steps
- open WinSCP
- set up new connection "SFTP://localhost:2222"
- edit to add private key file (SSH|Authentication|Private key file, and using sftp_rsa.ppk)
- connect by username foo

## SSH key pair
the following key pair is used for this demo
- run/sftp_rsa (private key, and sftp_rsa.ppk is converted from this private key file and used for WinSCP)
- run/sftp_rsa.pub (public key)

To generate new key pair, please use command as below in windows or linux
```
ssh-keygen -t rsa -b 4096 -f sftp_rsa
```

# code

## pom.xml
dependencies
- camel-spring-boot-bom (to introduce Camel BOM)
- camel-spring-boot-starter (to add Camel core)
- camel-ftp-starter (to add Camel sftp component)

camel.version
- the proper Camel version to use can be found through spring initializr

## DemoRoute.java
The demo class for Camel sftp route

## src\main\resources\application.properties
settings for sftp



