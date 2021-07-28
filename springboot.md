# Spring Boot Cheat Sheet

## Build
```
./mvnw package
```
```
./mvnw spring-boot:repackage
```

## Run
```
./mvnw spring-boot:run
```
```
./mvnw package
java -jar target/<jarname>.war
```

## Multiple Main Classes
```
<properties>
    <start-class>com.manifestcorp.demo.mq.mqdemo.MqDemoApplication</start-class>
</properties>

```
```
java -cp target/<jar> -Dloader.main=<main class> org.springframework.boot.loader.PropertiesLauncher

```
