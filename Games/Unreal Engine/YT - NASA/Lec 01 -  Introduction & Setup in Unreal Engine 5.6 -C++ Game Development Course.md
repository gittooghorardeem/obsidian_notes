
**YT Channel** : [NASA](https://www.youtube.com/@na12672/videos)
**Tutorial Vid** :   
[Introduction & Setup in Unreal Engine](https://youtu.be/hJriLkYFGdY?si=ZjF5A8Hg0-YF6w38) 


---------

- Create a Project using *3rd Person Template*
- *IntroProject*
- Gizmo 
	- X : Red
	- Y : Green
	- Z : Blue
- in Unreal : `1 unit = 1 centimeter`
- **Source code**
	- C++
	- file extension `.cpp` `.h`
- **Compiler**
	- Creates an executable file (`.exe` for windows)
	- **Visual Studio** for Windows (*Visual Studio 2022* community version)
	- **XCode** for Mac
	- **IDE** : Visual Studio and XCode


> **C++**

- Create a new Cpp project using *First Person Template*
- *IntroProjectCpp*
- In Visual Studio, `Games` folder
- `Games > Source` Source code created by the *FirstPerson Template*
- Code snippet : 
	- `UE_LOG(LogTemp, Display, TEXT("Hellow Game World"))` >> this will shown in the `OutputLog` of *UE editor* when this is called
	- Save > Close UE Editor
	- Build Config :  `Development Editor` and `Win64`
	- `Games > IntroProjectCpp` > `RMB` > *Rebuild*
	- After successful Rebuild, launch  `IntroProjectCpp.uproject` from Project Folder
- **C++ and Blueprint**
	- C++ and BP complement each other and are meant to be used together
	- *Blueprint* Pros
		- Easier to learn than C++
		- Programmed inside Unreal 
		- Quick to make changes. good for prototyping 
		- Writing gameplay code
		- ---
		- Blueprints -> `C++ Code`
			- -> `Unreal Engine Libraries`
	- *C++* Pros
		- Gives full control over all areas of Unreal and beyond
		- Much faster than anything written in BP
		- More Concise 
		- Better for writing bigger games and non-gameplay code
		- ---
		- `C++ Code` -> `Unreal Engine Libraries`

