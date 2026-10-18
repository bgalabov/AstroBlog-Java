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

![Boy, setting up Java and IntelliJ](/assets/images/environment-setup/boy-installing-java-intellij.webp)

Environment Setup
====================

In order to be able to run the exercises in this course you will need the following tools on your PC: 

1. Java SE Development Kit 8 *(JDK 8)*. 
2. IntelliJ IDEA 2026 *(you can use older version)*

## Table of contents

## 1. Setting up Java SE Development Kit 8 (JDK 8)

You can install Java SE Development Kit 8 in two alternative ways: 
- [**Standard installation**](#standard-installation) - by downloading and running an Installer program
- [**Advanced installation**](#advanced-installation) - by downloading an archive containing JDK, which you manually extract and manually setup your environment. 

### Standard Installation

1. You can download it from here: https://www.oracle.com/java/technologies/downloads/#java8

2. Select the Windows x64 installer: *jdk-8u503-windows-x64.exe*

3. Once the download is complete, run the installer. You should see the below screen (or similar): 

![JDK Installer screen](/assets/images/environment-setup/installer-1.png)

4. Click *Next*. On this screen, the Installer asks you which part of the JDK installation you want to install. Leave the default settings unchanged. Click *Next*.


![JDK Installation setup](/assets/images/environment-setup/installer-2.png)

5. On this screen, the Installer asks you if you want to change the target directory of the JDK installation. It is recommended to keep the default installation directory.  

![JDK Installation directory](/assets/images/environment-setup/installer-3.png)

6. Click *Next* and the installation will begin. After it is complete, you should see the following screen: 

![JDK Setup Completed](/assets/images/environment-setup/installer-4.png)

---

### Advanced Installation

This is an alternative to the [Standard Installation](#standard-installation). 
In summary, with this approach you download an archive, which contains JDK. After that you have to extract it and do a few manual configurations. 

1. You can download it from here: https://www.oracle.com/java/technologies/downloads/#java8

For Windows, we get the *x64 Compressed Archive* option, as by 12.10.2026, the following archive contains the latest version: **jdk-8u503-windows-x64.zip**

2. Extract the file to `C:\jdks`. 

Once you have extracted the archive, you should be able to browse the directory where you had extracted the archive: 

![JDK path](/assets/images/environment-setup/jdk-path.png)


Copy the path, as on the screenshot above. 
In my case, this is: `C:\jdks\jdk-8u503-windows-x64\jdk1.8.0_503`

In the below steps, we need to configure two Environment Variables: 

- `JAVA_HOME` is an environment variable that points to the directory where the Java Development Kit is installed.
- The `Path` environment variable tells Windows where to look for executable programs when you type commands in the terminal.

Adding `%JAVA_HOME%\bin` to Path allows us to execute commands such as `java` and `javac` from any directory without specifying their full paths.

3. Now, Right-click the *This PC* icon on your Desktop and select -> *Properties*. Click on *Advanced system settings*:

![Advanced system settings](/assets/images/environment-setup/advanced-system-settings-option.png)

4. A *System Properties* window opens. Now, click on *Environment Variables*. 

![System Properties](/assets/images/environment-setup/system-properties.png)

5. Now, we need to add a new *System variable*, select the *New...* button on the bottom of the window: 

![New Variable](/assets/images/environment-setup/new-variable.png)

6. The variable we want to add is called `JAVA_HOME`. Its value should point to the installation of Java Development Kit, in my case, this is: 

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

You should see the installed Java compiler (`javac`) and runtime versions (`java`). 

---

## 2. Setting up IntelliJ Idea 2026

1. Download **IntelliJ IDEA** from the official website: 
https://www.jetbrains.com/idea/download/

In this guide we cover the installation via Installer (.exe) .

2. Once the download is complete, run the installer: 

![IntelliJ IDEA Installer](/assets/images/environment-setup/intellij-installer-1.png)

3. Select *Next*.  On the next screen, the Installer asks you if you want to change the target directory of the IntelliJ IDEA installation. It is recommended to keep the default installation directory: 

![IntelliJ IDEA Installer - Installation Directory](/assets/images/environment-setup/intellij-installer-2.png)

3. On this screen, the Installer asks you for a few installation settings. Select the *Create desktop shortcut: IntelliJ IDEA* option. 

![IntelliJ IDEA Installer - Installation Directory](/assets/images/environment-setup/intellij-installer-3.png)

4. Select *Next*. On this screen, the Installer lets you to reject the creation of *IntelliJ IDEA* shortcuts within the Start-menu of Windows. It is recommended to keep the default setting: 

![IntelliJ IDEA Installer - Installation Directory](/assets/images/environment-setup/intellij-installer-4.png)

5. Select *Install*. It may take a few minutes for the installation to complete. After finished, you should see the following screen: 

![IntelliJ IDEA Installer - Installation Directory](/assets/images/environment-setup/intellij-installer-5.png)

6. Select *Finish* and **IntelliJ IDEA** will start. 

7. **IntelliJ IDEA** will ask you for permission to share anonymous data about how you use the software. Personally, I choose *Don't Send*: 

![IntelliJ IDEA - Data Sharing](/assets/images/environment-setup/intellij-1.png)

8. **IntelliJ IDEA** will ask you whether you want to import settings from other tools, like **VS Code**. Personally, I choose *Skip Import*. 

![IntelliJ IDEA - Import Settings](/assets/images/environment-setup/intellij-2.png)

9. **IntelliJ IDEA** launches and with the below initial screen: 

![IntelliJ IDEA - Initial Screen](/assets/images/environment-setup/intellij-3.png)


10. Select *New Project*. The following screen is shown: 

![IntelliJ IDEA - Create Project](/assets/images/environment-setup/intellij-4.png)


Here, there are the following fields: 

- **Name** - the name of your Project
- **Location** - the directory where the Project structure will be created. By default, this is your user folder: *C:\Users\<windows_user_name>\IdeaProjects*
- **Build system** - here we do not change anything. Keep it *IntelliJ*
- **JDK** - the Java Development Kit version your project will work with. **IntelliJ** can auto-detect installed JDKs. You should see them under *Registered JDKs*. If you had installed JDK using the [**Standard Installation**](#standard-installation), it shoud appear here automatically. 

In case it does not apper, or you had performed the [**Advanced Installation**](#advanced-installation), select *Add JDK from Disk...* and select the directory of your JDK installation from the disk. 

For example: `C:\jdks\jdk-8u503-windows-x64\jdk1.8.0_503`

The selected JDK should now appear in the list. 

11. Select *Create* and **IntelliJ IDEA** will create your project. 

In case you want to Close your current project or create a new one, you can click on the Sandwich menu on the top left corner and select *Close Project* or *New* -> *Project*.   

![IntelliJ IDEA - Create Project](/assets/images/environment-setup/intellij-4.png)

If you choose *Close Project*, the initial screen from step **9.** will appear, showing you all of the projects within the current **Location** directory. 

**Happy Coding!**














