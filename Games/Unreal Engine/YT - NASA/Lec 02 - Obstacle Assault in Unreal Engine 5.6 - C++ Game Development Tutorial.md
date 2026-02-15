**YT Channel** : [NASA](https://www.youtube.com/@na12672/videos)
**Tutorial Vid** : [Obstacle Assault in Unreal Engine 5.6](https://youtu.be/xXUl3J_-JPY?si=ql4bXgxv1r-lUJq_)  


-----
> **Action plan**

- Create a new project and setup a test level
- Learn some C++ basics 
- Create a platform that moves
- Rotate platform 
- Import assets and design a level

**Create a new project**
- Create a new `C++` project with *3rd person template*
- Project `ObstacleAssault`
- Create a folder `MyStuff` inside the default `Content Folder`
- Create a New Level > `Basic` template
- Save the Level `TestLevel` inside `MyStuff`
- *Project settings* >  Update **Game Default & Startup Map** > `TestLevel`

**Geometry Brushes to create complex Shapes**

- Add an actor `Geometry > box` to the `TestLevel`
	- *Geometry Brushes* : 
		- Do not change the attributes of `Transform`
		- `Box Settings`
			- x : 1000
			- y : 60
			- z : 400
	- *Brush Type* :
		- *Subtractive* : Subtractive removes the geometry from the additive ones
		- *Additive* : Adds

**Create C++ Classes**
- **UE Editor** > *Tools* > *Create new class* 
	- Parent class : `Actor Class` > `MovingPlatform`
	- `MovingPlatform.h` and `MovingPlatform.cpp` files get added to the source code *ObstacleAssault > Source > ObstacleAssault*
- `.h` (*header file*) `.cpp` (*C++ file*)
	- `.h`
		- Think of it as like a *Menu*
		- What this class has : *Data, Variables, Functionality or functions* 
		- Does not define any of them, just shows what this class has
		- Decoration of the class
		- Functions are declared but not explained what they do
	- `.cpp`
		- Actual codes which we are going to write
		- Functions behaviors are written here

**Live coding**

- Live coding lets us compile the project without exiting the editor or without going into Visual Studio 
- Enable Live Coding 
  ![[LiveCodingPanel.png]]
- *Change source code then Live Coding to compile it*
- Live Coding is **BEST** when changes are made in the `.cpp` files
- Best Practice to use **Visual Studio** to compile changes in the `.h` files
- *Recompile* using **Visual Studio** at the *End of the Work session* or at the *Start of the New one*

**Variable and DataTypes**

- Data Type : `FString` - Unreal Specific 
- Format Specifier : 
	- `UE_LOG(LogTemp, Display, TXEXT("Number of Apples %d"));`
		- `%d` =  want to place a Variable in side this '`d`', and '`d`' means this variable is an `Integer`
		- `%f` = Similar to above, '`f`' means the variable is a `Float` point number
		- `%s` = '`s`' means the variable is a `String` type. 
			- Need to put an * in front of the Variable name
			  `UE_LOG(LogTemp, Display, TEXT("My name is %s"), *MyName);`
		- `%c` = To print out a `Character`
		- `%p` = To print out memory location  

**Basic Mathematical Operations**

**Operator Precedence**

- Sequence : *Multiplication* > *Division* > *Addition* > *Subtraction* 
	- *Parenthesis* '`( )`' overrides the previous precedence  

**Member Variables**

- *Local Variables*
	- Only be accessed in the function they are created in 
- *Member variables* 
	- Member variables are declared in the *Header* file
	- Member variables *retain* their Data
	- They are accessible in all of the function of the class
	- *Registering with Unreal*
		- `UPROPERTY` macro is used to register a *member* variable with the Unreal Engine
		- This lets us see and edit the variable in the editor 
		  `class AMovingPlatform
		  `{`
			  `UPROPERTY(EditAnywhere)`
			  `float MyFloat;`
		  `}`

**Structs**

- A group of variable packaged together under one name
	  `struct FVector`
	  `{`
		  `float X:`
		  `float Y:`
		  `float Z;`
	  `};`
	  
	  FVector MyVector;
	  MyVector.X = 10.4f;
- In the UE editor *Transform* is a good example of a `Struct`

**Set Location of an Actor in C++**

- need to add a component in the `MovingPlatform` Actor class
- UE Editor : add a Cube Component to the `MovingPlatform`
- The First component added to an Actor is the *Root Component*

**Moving the Platform**

- *Game Loop*
	- All games use a Game Loop to function
	- this is a loop that runs continuously and updates the game
		- 1. Get Input
		- 2. Update Game State
		- 3. Render graphics to the Screen
- *Tick*
	- Each cycle of the game loop is called a Frame
	- The amount of frame you have in 1 second is called Frames Per Seconds (FPS)
	- Tick is a special function that is called every frame of the game

Start From : ~~`01:50:33`~~

**Move the platform from the Starting Position**

- `GetActorLocation()` : will give the current location of an Actor as FVector
	- This function returns a value to us
	- `Get` : returns a value
	- `Set` : Sets a value (`SetActorLocation`)
	  
	  `CurrentLocation = GetActorLocation();`

**Make the Game Framerate Independent (Delta Time)**

- *The Speed Problem*
	- Different computers will run the game at different speeds 
	- This creates a problem if we are adding or subtracting a value inside of the *Tick Function* 
- *Delta Time*
	- Use a special variable called `DeltaTime` to fix this issue 
	- Delta time is the amount of time it took the CPU to compute the last frame
		- 1. Get Input
		- 2. Update Game State 
		- 3. Render Graphics on the Screen
	- We can make operations like these frame rate independent by Multiplying the value we are adding with delta time
	- `DeltaTime `value is given by the *Unreal engine*, we do not need to calculate it 


**Velocity Vectors and Number operations on Structs**

- Create a Member Variable in the `MovingPlatform.h` file.
- Member Variable : `PlatformVelocity`
  `UProperty(EditAnywhere)`
  `FVector PlatformVelocity = FVector(0.0f, 0.0f, 0.0f);`
- In the `MovingPlatfomr.cpp` file 
	- `CurrentLocation = CurrentLocation + (PlatformVelocity * DeltaTime);`
- From UE editor update the `PlatformVelocity` from `MovingPlatform` Actor Class details section.

**Functions**

- Create a New function in the `MovingPlatform.cpp` file
- `MyTestFunction() {--- Log message ---}` over `BeginPlay()` function 
- Call the `MyTestFunction()` inside `BeginPlay()` function

~~Start From `02:24:50`~~

**Function Parameters**

- function `GetName()` - Will return the name of this actor. 

**Member Function**

- Member functions can be defined anywhere in the `.cpp` file unlike normal functions which needs to be defined before `BeginPlay()` member function
- Member Function is a function that belongs to a Class
  
  *Header File* : Declaration 
  `class AMovingPlatform`
  `{`
	  `void MemeberFunction(float MyParam);`
	  `}`
	  
	*C++ File* : Definition 
		`void AMovingPlatform : : MemberFunction(float My Param)`
		`{`
			`fVector MyLocation = GetActorLocation();`
			`SetActorLocation(MyLocation * 2.0f):`
			`}`
 

- Create a Member function : 
	- `.h` file : `void MovePlatform(float DeltaTime);` 
	- `.cpp` file : 
		- Make MovePlatform a Member function by link it with the class
		  `void AMovingPlatfomr : : MovePlatform(float DeltaTime) { --- }`
		- Cut paste the platform movement code from Tick() function in side the `MovePlatfomr()` member function 
		- Call the `MovePlatform()` function inside `Tick()`
		  `MovePlatfomr(DeltaTime)`
- Create a Member function to Rotate the Platform
	- Create a Function `RotatePLatform(DeltaTime)` in the `.h` file
	- Create a Member variable
		- `UPROPERTY(EditAnywhere)`
		  `FRotator PlatfomrRotator = FRotator(0.0f, 0.0f, 0.0f);`
	- Define the Member function `RotatePLatform(DeltaTime)` in the `.cpp` file
		- Add a `FRotator` Variable `CurrentRotation`
		- `GetActorRotation()` and `SetActorRotation()`
	- Call `RotatePLatform(DeltaTime)` in side of `Tick()` function

**Classes and Instances**

**Blueprint Child Classes**

- *C++ Class > Blueprint Child Class > Instances created from Blueprint Child Class*
- Move to the *MyStuff* folder
- Create a Blueprint `MovingPlatfomr` class > `BP_MovingPlatfomr`

**Platform Move Distance and Scope Resolution Operator**

-  Platform *Start Location* and *Distance Moved*
- Create a Member variable in the `.h` file, no need to *UPROPPERTY* and *Default values*
  `FVector StartLocation;`
- In `.cpp` file `BeginPlay()`
	- `StarLocation  = GetActorLocation();`
- in `.h` Create a `UPROPERTY(VisibleAnywherw)` member variable > 
  `float DistanceMoved = 0.0f;`
- *Scope Resolution opertor*
	- `.cpp` > `MovePlatform()`
	- `DistanceMoved FVector :: Dist(StartLocation - CurrentLocation);` -> Returns *float*


~~Start From `03:08:59`~~

**'If' Statement for moving platforms to cycle the movement**

- Comparison Operators : These operator take 2 values, compare them and evaluate o Boolean value
	- `==` : Equal 
	- `!=` : Not Equal
	- `>` : Greater than
	- `<` : Less Than 
	- `>=` : Greater or equal to 
	- `<=` : Less or qual to 
- `.h` file : Create a UEPROPERTY Member Variable : `MovedDistance`
- `.cpp` file : in `MovePlatform()`
	- `if (DistanceMoved >= MovedDistance)`
	  `{`
		  `PlatfomrVelocity = - PlatfomrVelocity;`
		  `StartLocation = CurrentLocation;`
		  `}`

**Overshoot Problem for the Platforms**

- Overshoot correction : 
	- *StartLocation = StartLocation + MovedDistance * Direction*
- in `.cpp` file create 2 variables in `MovePlatform()`
	- `float OverShoot = DistanceMoved - MovedDistance` 
	- `FString PlatformName = GetName()`
- ![[MovePlatform_Overshoot_correction.png]]
**Rotate Platform**

- `void AMovingPlatform::RotatePlatform(float Deltatime)`
	`{`
	`// Rotate the Platform`
	`FRotator  RotationToAdd = RotationVelocity * Deltatime;`

	`AddActorLocalRotation(RotationToAdd);`
	`}`

**Function Return Values**

**Converter to Function**

**Import Assets from FAB library**

- FAB Library : 
	- Environment : *Stylized Eastern Village*
	- Character : *Survival Character*
	- Props : *Construction Site Vol 1*
- 

**Level Designing with the asset packs**

- Moving the Gizmo in the center of the object
	- Object Blueprint
	- Align the object mesh center with the default scene root center 

~~Start From `03:59:03`~~

**Player actions tweaks**

Start From `04:04:18`

>            --- **IMPORTANT**---

**NEED TO RECRETE THIS LEC 02 AGAIN AS MY SYSTEM CRASHED AND AFTER REINSTALLING THE CODE IS FAILING TO BUILD SUCCESSFULLY**