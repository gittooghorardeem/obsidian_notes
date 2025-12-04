
> **Setup** **Requirement**

- Java
- Node
- npm
- Android Studio
- Android SDK platform Tools 
	- Unzip
	- Update Environment Variable 
		- System Var - `path`
- Install Appium
	- `npm install appium`
- Install `apk info` from google playstore
- ANDROID_HOME
- MAVEN_HOME
- JAVA_HOME
- check after setup Env Variables (terminal)
	- `echo %JAVA_HOME%`
	- `echo %ANDROID_HOME%`
	- `echo %MAVEN_HOME%`

> **Setting up for macOS**

- **JAVA_HOME**
	- JAVA_HOME - 
		- terminal `/usr/libesec/java_home -V`
		- copy `/Library...virtualmachines/`
		- cmd+shift+N+G : brings up a nifty go to location option
		-  Go to that folder and navigate to `jdk-xx.jdk/contents/home/bin/`
		- copy the `bin` folder location
		- in terminal : 
			- `echo $JAVA_HOME` : shows any existing paths
			- `export JAVA_HOME=<paste the copied path>` hit enter
			- `echo $JAVA_HOME` : confirm to check whether the paths is pasted properly
			-  FUCK!! the idiot showed this setup for only that active session 
			- **Permanent set**
			- `echo $SHELL`
			-  create .zshrc file in pwd : /Users/ghorardeem location
			-  `nano .zshrc`
				- provide :
				  `export JAVA_HOME=<paste the copied path>`
				  `export PATH="<pasted the copied path>/bin:$PATH"`































   