# Web and Mobile Framework Repository for Automatic Testing

This repository contains all necessary tools and features for the automation of front end
applications. With the use of
environment variables in
IntelliJ IDEA, you can easily switch between running tests for web or mobile platforms and choose a
cloud testing provider as SauceLabs or keep running in Local. Also is
integrated with axe-core
tools to easily check web accessibility violations while running an automated web script.

## Getting Started

To set up your local environment and install dependencies for running the tests, follow these steps:

## Pre-requisites

Ensure you have IntelliJ IDEA installed on your system.
Make sure you have Maven installed, Git and Java jdk 11 or superior.
Have a GitHub account with a Personal Access Token.

IntelliJ Idea Community: https://www.jetbrains.com/idea/download/?section=windows

Maven: https://maven.apache.org/download.cgi

Java: https://www.java.com/es/download/ie_manual.jsp

Git: https://www.git-scm.com/downloads

## Setting Up GitHub Packages

To download the required Maven packages from GitHub Packages, follow these steps:

Step 1: Generate a new Personal Access Token

Go to your personal GitHub account and create a new token with read packages permission.
Copy your token for the following step.

Step 2: Configure GitHub authentication

Create or update your `settings.xml` file in the `.m2` directory (usually located in your home
directory) with the following content:

```xml

<settings xmlns="http://maven.apache.org/SETTINGS/1.2.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.2.0 http://maven.apache.org/xsd/settings-1.2.0.xsd">

    <servers>
        <server>
            <id>github</id>
            <username>YOUR_GITHUB_USERNAME</username>
            <password>YOUR_GITHUB_TOKEN</password>
        </server>
    </servers>

</settings>
```

Replace YOUR_GITHUB_USERNAME with your GitHub username and YOUR_GITHUB_TOKEN with a personal access
token generated from your GitHub account with read:packages permissions.

### Install User Certificate in Git

Open the following
link: https://everisgroup.sharepoint.com/sites/Zscaler/Shared%20Documents/Forms/AllItems.aspx?id=%2Fsites%2FZscaler%2FShared%20Documents%2FKnown%20Issues%2FFixes%2FWindows&viewid=a2c69b76%2Dc9ca%2D4e54%2D987b%2D3c3835a729e3
Locate the file named "Zscaler_USER_EnvironmentVariables.exe", download it to your computer and execute it.

## Setting Up Appium Environment

Step 1: Install Node.js
Appium runs on Node.js. If you don't already have Node.js installed, download and install it
from https://nodejs.org/en/download.

Step 2: Install Appium

Install Appium globally using npm (Node Package Manager). Open your terminal or command prompt and
run the following
command:

`npm install -g appium`

Step 3: Install Appium Dependencies

Appium has specific dependencies for different mobile development platforms. Install the necessary
dependencies based on
the platform you want to automate tests for.
In the next lines you will install this different dependencies.

Run on terminal the command: `appium driver install uiautomator2` to install a necessary driver.

### Android

Install Android Studio following the instructions on https://developer.android.com/studio/install.
Set up `ANDROID_HOME` and `JAVA_HOME` environment variables correctly in user variables.

Step 4: Set Up Emulators or Physical Devices

Create a new project, select "No activity" option and follow the default configuration.  
Once you have Android Studio configured, go to *Settings*, search for *Android SDK Command-line
Tools* and apply changes.  
Use Virtual Device Manager tool from Android Studio to start a customized Android emulator.

### Install User Certificate for Android Studio

Open the following
link: https://everisgroup.sharepoint.com/sites/Zscaler/Shared%20Documents/Forms/AllItems.aspx?id=%2Fsites%2FZscaler%2FShared%20Documents%2FKnown%20Issues%2FCA%5FCertificates&viewid=a2c69b76%2Dc9ca%2D4e54%2D987b%2D3c3835a729e3
Locate the file named "Zscaler_Root_CA.exe " and download it to your computer.

Launch Android Studio in your computer and open the Device File Explorer. Navigate to the sdcard/Download Folder (
Right-click in the Download folder, select Upload) and navigate to the location where you saved the Zscaler_Root_CA.cer
file on your computer. Click open to upload it to the device.

Step 5: Start Appium Server

Run on terminal the command: `appium` to start appium server

## IDE Configuration

### Install User Certificate for IntelliJ

Open the following
link: https://everisgroup.sharepoint.com/sites/Zscaler/Shared%20Documents/Forms/AllItems.aspx?id=%2Fsites%2FZscaler%2FShared%20Documents%2FKnown%20Issues%2FFixes%2FWindows&viewid=a2c69b76%2Dc9ca%2D4e54%2D987b%2D3c3835a729e3
Locate the file named "Zscaler_ADMIN_Update_Java_CACERTS.exe ", download it to your computer and execute it.

### Configuration Steps

Create a new folder and clone the Repository:

`git clone https://github.com/raunelgarcia/front-end-automation.git`

Open Project in IntelliJ IDEA:

Open IntelliJ IDEA and select File > Open.

Navigate to the directory where you cloned the repository and select it.

### Configure SDK

Go to File > Project Structure
Click on the project SDK field. If the Amazon Correto SDK in not listed, select Add SDK > Download JDK. Select Amazon
Corretto, version 11.
Apply and confirm the configuration

## Set Environment Variables:

You can set environment variables in IntelliJ IDEA by going to Run > Edit Configurations > Add JUNIT
Configuration >
Environment.

#### Environment Variables:

- Platform:
    - Possible values: Android, IOS, Web.
    - Description: Specifies the platform for testing, whether it is Android, iOS or Web. Must be
      provided with valid values for the tests to function correctly.
- Accessibility:
    - Possible values: true, false.
    - Description: indicates whether accessibility features are enabled during testing. The variable
      can take the value of null or blank, in which case the Accessibility report will not be shown.
- Browser:
    - Possible values: Chrome, Firefox, Edge, Safari.
    - Description: Defines the browser to be used for web testing. The 'Browser' variable can take the value of 'null',
      in which case the default browser used for testing is 'chrome'.
      If you are using Safari for MacOS, write this command for enable the automatization: `safaridriver --enable`
- Application:
    - Description: Should be the name of the web app being tested. Application cannot be
      null and must be provided with valid values for the tests to function correctly.
- Resolution:
    - Possibles values: the possibles values of the environment variable resolution are established
      in the 'allowedResolution.yaml'.
    - Description: Specifies the screen resolution for web testing. If null or blank, a default
      resolution of 1024x768
      is set.
- Language:
    - Possibles values: en-GB, en-US, es-ES, fr-FR and others.
    - Description: Specifies the language of the test execution. If null or blank, the default
      language is es-ES.
- App:
    - Description: Specifies the path or name of the APK or .IPA file to be installed and tested on
      an Mobile device.
      The tests work if either the App field is set, or both AppPackage and AppActivity fields are
      provided (only
      Android).
- AppActivity:
    - Description: Represents the app activity for Android of the app being tested for mobile
      testing. The tests work if
      both AppPackage and AppActivity fields are provided.
- AppIdentifier:
    - Description: For Android it represents the app package and for IOS it represents the bundleId
      of the app being tested for mobile testing. The Android tests work if both AppPackage and AppActivity fields
      are provided.
- Udid:
    - Description: Represent the unique device identifier (UDID) of the device being tested for
      mobile testing.It can be obtained running on terminal `adb devices`. Must be provided with valid values for the
      tests to function correctly. For Android, in the variable takes the value of 'null', the default value is the
      current emulator Udid. For IOS, the Udid cannot be 'null'.
- Provider:
    - Possible values: Local and SauceLabs
    - Description: Specifies the provider or environment to launch any test execution. Could be made
      on SauceLabs or Local Environment.
- User:
    - Description: Represents the username of your SauceLabs Account.
- AccessToken:
    - Description: Represents the API access token of your SauceLabs Account.

Ensure to set these variables according to your testing requirements before executing the tests.

### Android Variables Example

Case 1: With AppActivity and AppPackage.
AppActivity=.activities.MainContainerActivity;AppIdentifier=com.iphonedroid.marca;Platform=Android;Udid=;Provider=;

| Campo         | Valor                             |
|---------------|-----------------------------------|
| AppActivity   | .activities.MainContainerActivity |
| AppIdentifier | com.iphonedroid.marca             |
| Platform      | Android                           |
| Udid          |                                   |

Case 2: With App.  
App=marca-com-7-0-20.apk;Platform=Android;Udid=;

| Campo    | Valor                     |
|----------|---------------------------| 
| App      | com.iphonedroid.marca.apk | 
| Platform | Android                   |
| Udid     |                           |

### IOS Variables Example

AppIdentifier=com.marca.marcador;Platform=IOS;Udid=A308507F-99BB-47A2-9A2D-06005CAAD428;Provider=;

| Campo         | Valor                                |
|---------------|--------------------------------------|
| AppIdentifier | com.marca.marcador                   |
| Platform      | IOS                                  |
| Udid          | A308507F-99BB-47A2-9A2D-06005CAAD428 |

### Web Variables

Accessibility=true;Platform=Web;Application=mrc;Browser=chrome;Resolution=1920x1200;Provider=SauceLabs;User=;AccessToken=;

| Campo         | Valor     |
|---------------|-----------|
| Accessibility | true      |
| Platform      | Web       |
| Application   | mrc       |
| Browser       | chrome    |
| Resolution    | 1920x1200 |
| Provider      | SauceLabs |
| User          |           |
| AccessToken   |           |

### Install Dependencies:

Open the pom.xml file in IntelliJ IDEA. Click on the 'Maven' tab, then click on the 'Reimport'
button to install all the
required dependencies.

### Configure Mobile Testing Environment (For Mobile Tests):

Before running mobile tests, ensure that you have:

- Mobile Platform Setup: Make sure you have the appropriate emulators, simulators, or physical
  devices configured and
  available for testing.

- Environment Configuration: Configure the mobile platform-specific settings in the
  mobileConfiguration.yaml file
  located in the project directory (resources/yaml/mobileConfiguration.yaml). Ensure that the
  required capabilities are
  correctly specified for Android and iOS platforms.

You can now run the automated tests either for web or mobile platforms based on the environment
variable you've set.

### Test Structure

src/test/java contains all the test classes.

src/test/resources contains apks, ipas and properties files for handle multilanguage texts.

### Using Allure Reports

If you want to generate reports with Allure, the framework is ready for it. Beforehand, some
preliminary configurations
need to be done.

Install Allure in the project using on terminal the
command `npm install --save-dev allure-commandline`

Once it's installed and when the test is executed, the results will be saved in
target/allure-results. A browser window
will open automatically after few seconds, displaying the Allure report.
Tests that encountered errors will have an error message displayed in the description section along
with a screenshot
pointing the location of the error. Also, Network logs will be attached to the report with all https
API requests made by the front end application and will be saved in network-logs directory

### Accessibility Reports

When the "Accessibility" variable is set to "true", accessibility reports will be generated and
saved in a folder
named "target/java-a11y".These reports provide insights into the accessibility status of your
application, helping to
ensure compliance with accessibility standards.

#### Report Formats:

The accessibility reports are available in two formats:

1. HTML Reports: These reports are human-readable and can ve opened in any browser. They provide
   detailed information
   about accessibility issues found during testing.
2. JSON Reports: These reports contain machine-readable data about accessibility issues detected in
   the application.

To access these report navigate to the "target/java-a11y" folder. You can open the HTML reports in
your preferred web
browser to review the findings.

### Contributors

Raunel Garcia Quintana

Raul Galera Sancho

Alejandra Alvarado Tirado

Leire Fuchun Jimenez Gonzalez

Ciro Alonso Aquino

### Acknowledgments

Special thanks to our contributors and the open-source community for their valuable contributions
and support.

