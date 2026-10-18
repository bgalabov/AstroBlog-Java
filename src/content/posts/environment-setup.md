---
author: Borislav Galabov
pubDatetime: 2026-10-03T10:40:08Z
modDatetime: 2026-10-08T20:59:05Z
title: Environment setup
slug: environment-setup
featured: true
draft: false
tags:
  - java
  - environment-setup
  - beginner
description: Environment Setup for the Platform Independent Programming Languages course. 
---

![Boy, programming in Java](/assets/images/exercise-1/boy-programming-in-java.webp)

Environment Setup
====================

In order to be able to run the exercises in this course you will need the following tools on your PC: 

1. Java SE Development Kit 8 *(JDK 8)*. 
2. IntelliJ Idea 2026 *(you can use older version)*



## Table of contents

## Setting up Java SE Development Kit 8 (JDK 8)

1. You can download it from here: https://www.oracle.com/java/technologies/downloads/#java8

For Windows, we get the *x64 Compressed Archive* option, as by 12.10.2026, the following archive contains the latest version: **jdk-8u503-windows-x64.zip**

2. Extract the file to `C:\jdks`. 

After you extract the archive, you should be able to browse the directory where you had extracted the archive: 

![JDK path](/assets/images/environment-setup/jdk-path.png)

Copy the path, as on the screenshot above. In my case, this is **C:\jdks\jdk-8u503-windows-x64\jdk1.8.0_503**

3. Now, Right click on the *This PC* icon on your Desktop and select -> *Properties*. Click on *Advanced system settings*:

![Advanced system settings](/assets/images/environment-setup/advanced-system-settings-option.png)

4. A *System Properties* window opens. Now, click on *Environment Variables*. 

![System Properties](/assets/images/environment-setup/system-properties.png)

5. Now, we need to add a new *System variable*, select the *New...* button on the bottom of the window: 

![New Variable](/assets/images/environment-setup/new-variable.png)

6. The variable we want to add is called `JAVA_HOME`. It's value should point to the installation of Java Development Kit, in my case, this is: 

`C:\jdks\jdk-8u503-windows-x64\jdk1.8.0_503`

![JAVA_HOME environment variable](/assets/images/environment-setup/java-home.png)

7. Now, we need to modify the `Path` system variable: 

![Modify Path environment variable](/assets/images/environment-setup/modify-path-env.png)

8. Click on *New* and put the following as a value: 

```
%JAVA_HOME%\bin
```

It should look something like below: 

![JAVA_HOME bin](/assets/images/environment-setup/java-home-bin.png)


9. Open `cmd` (Command Prompt) and type: 

```shell
javac -version
```

and

```shell
java -version
```

You should see the Java Compiler (`javac`) and Java Virtual Machine (`java`) versions. 





