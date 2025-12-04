> **Youtube**

- https://youtu.be/kBESOqobduE?si=U9SP7dMB0VZJeEaK

> **Useful links**

- adb command list - https://teamandroid.com/adb-commands-list/

> **Basic Tidbits** 

- Some of the Capabilities need to keep eye on
	- deviceName 
	- udid - the shows up when using `adb devices`
	- platformName - Android
	- platfromVersion - Android Version
	- automationName
	- appPackage
	- appActivity
- Project setup
	- **Maven**
	- Dependencies `<dependencies>`
		- google - Maven repository 
			- search : selenium java
			- search : appium -> java client 
	- Appium Drivers
		- https://appium.io/docs/en/2.3/ecosystem/drivers/
		- driver ; UIAutomator2 
			- require installation using terminal
			- `appium driver install <installation _key>`
		- `appium driver doctor uiautomator2`
- Type of apps
	- Native app : everything is with in the app
	- Hybrid App : Any action triggers browser window to open
	- Web App
- Few Testing scenarios 
	- Text Fields
	- switches 
	- radio button
	- images
	- scroll, tap, etc
	- examples on Native app
	- examples on Hybrid app
	- examples on web app 

> **Basic test setup**\

- Test Files should be located in > `src/test/java` folder
- Run the appium server (terminal)
- 