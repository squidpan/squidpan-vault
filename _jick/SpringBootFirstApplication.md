---
categories:
  - "[[Lessons]]"
tags:
  - lesson
author: []
url: ""
topics:
  - "[[Springboot]]"
created: 2025-12-04
title: My first Spring Boot Application using IntelliJ IDEA
last: 2025-12-04
subject: Simple Spring Boot Application - Spring Initializr and IntellijIDEA
---
# Summary

## Step 1: Access Spring Initializr

[Spring Initialzr](https://start.spring.io/)

## Step 2: Configure Project Metadata

a. Fill in the project metadata:
Project: Select Maven Project.
Language: Select Java.
- Spring Boot: Choose the latest stable version (e.g., 4.0.0).
- Group: Enter your group name (e.g., com.squidpan).
- Artifact: Enter your artifact name (e.g., SpringBootFirstApplication).
- Name: Enter your project name (e.g., Spring Boot First Application).
- Package Name: auto-filled based on group/ artifact. I used **app** (.e.g. com.squidpan.app)
names.
- Packaging: Choose Jar.
- Java: Select your Java version (e.g., 25)

## Step 3: Add dependencies

## Step 4: Generate the Project

- Click on Generate. This will download a ZIP file named SpringBootFirstApplication.zip
## Step 5: Extract and Open Project

- Move ZIP to $SPRINGBOOT_MYIDEAPJS
- Extract ZIP
- Open it as Project in IntellijIDEA

## Step 6: Test it

- In SpringBootFirstApplication, add Hello World to see it works 

```code
package com.squidpan.app;  
  
import org.springframework.boot.SpringApplication;  
import org.springframework.boot.autoconfigure.SpringBootApplication;  
  
@SpringBootApplication  
public class SpringBootFirstApplication {  
  
    public static void main(String[] args) {  
  
        SpringApplication.run(SpringBootFirstApplication.class, args);  
        System.out.println("Hello World!");  
    }  
  
}
```


open terminal in IntelliJ

```code
./mvnw spring-boot:run
```