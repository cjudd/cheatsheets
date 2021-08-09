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

Maven
```
<properties>
    <start-class>${main class}</start-class>
</properties>
```
Gradle
```
springBoot {
	mainClass = '<main class>'
}
```

Run
```
java -cp target/<jar> -Dloader.main=<main class> org.springframework.boot.loader.PropertiesLauncher

```
