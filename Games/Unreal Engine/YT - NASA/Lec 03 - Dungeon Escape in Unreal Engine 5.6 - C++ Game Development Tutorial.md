**YT Channel** : [NASA](https://www.youtube.com/@na12672/videos)
**Tutorial Vid** : [# Dungeon Escape in Unreal Engine 5.6](https://youtu.be/qmlzAD3lvG8?si=48bVEeT7oEqmQgYv)  

**Summary** 

- Dungeon Puzzle game
- Solve puzzles to find items
- Place items to complete puzzle
- Inventory systems
- Movable planes in the game level
- Open and ending of the game

**Action Plan**

- Create a new project with the FPS template 
- Setup a cool test level from scratch 
- Learn about the lighting system in Unreal 
- Code the gameplay elements : Mover, Trigger, Pressure Plates, Item System etc. 
- Cover more on C++ and unreal basics etc
- Import assets and design the final level

--- ----


**Create a New Project**

- Create a new project using *First Person Template* using `C++` 
- Create a new folder **MyStuff** inside the content folder

**Create a New Blank Level**

- Create a new *Empty* level - `TestLevel`
- Set `TestLevel` as Default level from *Project Settings* 
- Add a `Geometry` Brush > `Box Brush`
	- Set the location of the Box Brush `0,0,0`
	- From *Brush Settings* update the scale `5000, 5000, 50`
	- Rename the `Box Brush` > `Ground`
	- make the viewport `Unlit`
	- Add a `Player Start` actor

**Lighting Setup**

- Add Lights 
	- `Directional Lights` :
	- `Sky Light`
- For Sky > 
	- `Visual Effects`
		- `Sky Atmosphere`
		- `Exponential Height Fog`
		- `Volumetric Cloud`
		- 
- `Sky Light`
	- Details > `Recapture`
		- after any changes made with the level's directional lights 
	- Details > **Check** `Realtime Capture`

**Mobility Settings of Lights**

- Set *Mobility* setting to `Movable` for
	- `Directional Light`
	- `Skyligh`
- Move all the lighting elements to `Lighting` folder

**Materials and Test Area**

- ***Starter Content asset pack***
	- *Add* > *Add Feature or Content Pack* > *Contents*
- Material assigning on actors 
	- Select the preferred material 
	- then add a Geometry Brush object
- Rename the `Box Brush` actor to `Room1`
- Add Door
	- `Subtractive brush` - *Box Brush*
- `Room1` Details section
	- *Hollow*
	- *Wall Thikness*


**Character Blueprint and GameMode**

- `Content > FirstPerson > Blueprint`
- Create a Child class from `BP_FirstPersonCharacter` > `BP_Player`
- Move `BP_Player` to `MyStuff` folder
- **Uncheck** the `Visible` settings for both of the meshes
- Open Starter `content > FirstPerson > Blueprint > BP_FirstPersonGameMode`
	- Game mode Classes setting Update the Default Pawn class > `BP_Player`

- *GameMode*
	- 

**Inheritance vs Composition**

- *Inheritance* : A child class automatically has all the functionality of the parent. The Child "is a" parent 
	- More rigid and strict
	- Cannot break the structure of the Hierarchy
- *Composition* :  Class A has an instance of Class B,  it can choose to use its functionality but doesn't have to. Class A "has a" Class B
	- More relaxed
- *Is-a*
  ![[Screenshot 2026-02-15 140053.png]]
- *Has-a*
  ![[Pasted image 20260215140755.png]]
  ![[Screenshot 2026-02-15 142252.png]]
  
**Create Mover Component**

- *Game plan* : Create a component that will move the actor of our choice 
- Place a Cube shape and transform it to a Door shape and rename `Room1_Door_Shape`
- Create a New Actor Component C++ Class `Mover`
- VS : `Mover.cpp` `Mover.h`
- Add `Mover` Actor component with the actor `Room1_Door_Shape`

**Pointers**

- *Variables in Memory*
	- Variables are stored in the memory of the Computer. 
	- All variable have an addresses 
	- This address is the location of this variable in the memory 
	- We can get this address with the `&` operator
	  
	  `float MyFloat = 10.5f;`
	  `&MYFloat; //Address of MyFloat`
	  `// Example address : 845600320`
- *Pointer*
	- A pointer is a type of variable 
	- it stores the address of a variable in memory, and it is used to access that variable 
	- to create a pointer use the * operator after the data type of the variable
	  
	  `float MyFloat = 10.5f;`
	  `float *PointerToMyFloat = &MyFloat;`
	- ![[Screenshot 2026-02-15 150358.png]]

- *Accessing Pointers*
	- * operator is used to dereference a pointer and access the value it is pointing to. 
	  
	  `float MyFloat = 10.5f;`
	  `float *PointToMyFloat = &MyFloat;`
	  
	  `float Value = *PointToMyFloat; // Value is 10.5f`
	  `*PointToMyFloat = 3.2f; // MyFloat is assigned to 3.2f`
- *Pointer Types* 
	- We can create pointer of any datatype.
	- C++ basic data types (int, float etc.), structs and classes 
	  
	  `FVector MyVector = FVector(1.0f,1.0f,1.0f);`
	  `FVector *PointerToMyVector = &MyVector;`
	  
	  `(*PointerTOMyVector).X = 2.0f;`
	  
	  C++ : `PointerTOMyVector -> Y = 5.0f;`
- *Advantages of Pointers* 
	- Lets say we want to create a copy of a variable 
	  int A = 10;
	  int B = A;
	- If you assign theoriginal to a new variable the entire memory will be copied 
	- This isn't a problem with the basic data types, but it becomes costly when dealing with larger types like classes/structs 

~~Start from `00:59:54`~~

- Never assign `null` to a pointer -> it will crash the game
- Assign `nullptr` when declaring a pointer variable.
- To print out memory address
	- `%p` -- 
	  `UE_LOG(LogTemp, Display, TEXT("*FloatPtr is %p"), FloatPtr);`
- Pointers mainly get used for `Structs` and `Classes` 
- Vector Log print : 
	- `MyVector.GetSafeNormal();`
	- `MyVector.ToCompactString();`
	- `VectorPtr->ToCompactString();`

![[Screenshot 2026-02-15 213627.png]]


**GetOwner() Function & move the Door Up* to the sky*

- `AActor* MyOwner = GetOwner();`
- `MyOwner->GetActorNameOrLabel();`
- Also `GetOwner()->GetActorNameOrLabel();`

~~Start from `01:14:47`~~

**Math Library Function** (*For the moving Door*)

- *Game Plan*
	- Move Offset
	- Target Location
	- Math Library Function
	- Boolean : Should Move
		- If true : Moves
		- if False : wont move
- In `Mover.h` file
	- *Member* variables : 
		- `StartLocation`
		- `TargetLocation`
	- *UProperty Member* Variable : 
		- `FVector MoveOffset;`
		- `float MoveTime = 5.0f;`
		- `bool ShouldMove = false;`
- in `Mover.cpp` file
	- `#include "Math/UnrealMathUtility.h"`
	- `BeginPlay()`
		- `TargetLocation = StartLocation + MoveOffset`
	- `TickComponent()`
		- `if (ShouldMove == true) {---}`
			- `FVector CurrentLocation = GetOwner()->GetActorLocation();`
			- `float Speed = MoveOffset.Length() / MoveTime;`
			- `FVector NewLocation = FMath::VInterpConstantTo(CurrentLocation, TargetLocation, DeltaTime, Speed);`
- `*FMath :: VInterpConstantTo()*`
	- Interpolate vector from Current to Target with Constant step
	- `FVector VInterConstantTo(current, target, DeltaTime, Speed)`

![[Screenshot 2026-02-16 121339 1.png]]

**Move Door Back n forth**

- ![[Door_moving_up_down.png]]


**Logical NOT Operator**

~~Start From `01:43:04`~~
- *NOT Operator* `!`
	- Reverse the Result 
	- Returns **False** if the result is *True*
	- Returns **True** if the result is *False*

**Compilation Process of C++ Unreal project**

- `Source Code`
	- Feeding all the source code to *Unreal Hader Tool* - Generate more C++ code
		- *Unreal Header Tool* -> Standard C++ Compilation
			- *Preprocessor* : 
				- `game.cpp, math.h, math.cpp` -> `game.i` , `math.i` intermediate file > Sends to *Compiler*
			- *Compiler* : Compile to Binary executable files and links to the Linker
				- `game.obj, math.obj` (Machine or Binary code files) > Sends to *Linker*
			- *Liner* : Gather all the executables and generate a singular Executable 
				- `---.obj` -> `game.exe` single executable
	- ![[Unreal_Cpp_Compilation_Process.png]]

**Trigger Components**

- **Action Plan**
	- Trigger as component added to Actors like Mover component
	- Trigger to have transform
	- Collision components 
	- Need to Use Box Component 
	- Connection with Mover components 
	- 2 different Gameplay elements 
		- 1. Pressure Plate
		- 2. Item Lock system

- Create a new C++ `BoxComponent` Class > `TriggerComponent`
	- C++ does not include the `Beginplay()` or `TickComponent()` function by default after creation. 
	- Copy paste the missing functions and attributes form `Mover.h` and `Mover.cpp` files 

**Trigger Component : Constructor function in C++**

- *Constructor*
	- Constructor is a special function belongs to a Class

**Connection Between Trigger and Mover components**

- *Action Plan*
	- Access to the Actor who owns the *Mover component* from the *Trigger Component*

Start From `02:11:21`