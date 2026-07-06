# Building and Packaging a Java Application with Gradle

This repository documents the step-by-step process of setting up, testing, building, and running a Java-based calculator application using **Gradle**. It also highlights a common Java Toolchain issue encountered during execution and how it was successfully resolved.

##  Step 1: Cloning the Repository


Clone the source code from GitHub:
```bash
git clone https://github.com/Ibrahim-Adel15/calculator-gradle.git
cd calculator-gradle
```
<img src="Screenshots/1.png" alt="1" width="500">

<img src="Screenshots/2.png" alt="1" width="500">

##  Step 2: Run the Unit Test

When attempting to execute the unit test using gradle test, the build failed with the following error:

<img src="Screenshots/3.png" alt="1" width="500">

As shown above, Gradle’s toolchain detected that the project strictly requires Java 17, which was missing from the local environment.
### Resolution Steps
    1- List Available Java Versions
    2- Install & Set Java 17 as Default
  <img src="Screenshots/4.png" alt="1" width="500">
  <img src="Screenshots/5.png" alt="1" width="500">

### Run the Unit Test again 
With Java 17 successfully configured, running gradle test compiled the test classes and completed flawlessly.

<img src="Screenshots/6.png" alt="1" width="500">

## Step 3: Build the Application Artifact
Package the project into a JAR file using Gradle:

<img src="Screenshots/7.png" alt="1" width="500">
<img src="Screenshots/8.png" alt="1" width="500">


## Step 4: Run the Application
Run the packaged Java application using: 
```bash
java -jar build/libs/calculator.jar
```
<img src="Screenshots/9.png" alt="1" width="500">

## Summary
- Clone the source code from GitHub
- Run the Unit Test
- Build the Application Artifact
- Run the Application
