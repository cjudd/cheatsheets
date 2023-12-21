# JHipster Cheat Sheet

## Resources
* https://www.jhipster.tech/
* https://start.jhipster.tech/jdl-studio/
* https://www.jhipster.tech/creating-an-app/

## Install JHipster
```
npm install -g generator-jhipster
```

## Create Project
```
mkdir myApp && cd myApp
jhipster
```
Model entities with [JDL Studio](https://start.jhipster.tech/jdl-studio/)
```
jhipster import-jdl jhipster-jdl.jh
```

## Run
```
./mvnw
npm start
```