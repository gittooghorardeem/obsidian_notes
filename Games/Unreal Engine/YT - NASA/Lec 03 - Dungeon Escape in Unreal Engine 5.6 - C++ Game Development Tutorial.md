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

~~Start From `02:11:21`~~
- `TriggerComponent.h` file
	- create a *UProperty* member variable `*MoverActor` 
		- `UProperty(EditAnywhere) AActor* MoverActor;` 
	- #inlcude `Mover.h` to `TriggerComponent.h` file
	- Create a Member Variable `*Mover`
		- `UMover* Mover;`
- Add any #include inside the `.h` file, always add before : 
	- `#include "TriggerComponent.generated.h"`
- `TriggerComponent.cpp` file
	- Check if the *TriggerComponent* pointer `MoverActor` is *null*
	- Check if the *Mover Component* pointer `Mover` is *null*
	- `Mover = MoverActor->FindComponentByClass<UMover>();`

![[null_check_for_Mover_Trigger_Components.png]]


**True False values in C++**

- In C++ 0(Zero) is used to represent `false`
	- `0, nullptr, NULL`
- Everything non-zero is `true`
- *Pointer*
	- A valid pointer has a non-zero value
	- A null pointer has a *false* value, because nullptr is zero
		- `AActor* MyActor = 0;`
		- `AActor* MyActor = nullptr;`
		- `AActor* MyActor = NULL;`

**Delegates/Events in C++ (Pressure Plate)** 

- *Delegates* are events that are *fired* when certain thing happens 
- Functions are able to be connected to these delegates
- When the delegate is fired connected functions are called
- *Overlap Events*
	- The Box Component has a delegate called 
		- `OnComponentBegingOverlap`
	- This Delegate is fired when something *overlaps* with this component
	- For example, the player walking into the trigger 
	- There is a similar delegate for when something stops overlapping
		- `OnComponentEndOverlap`
- ![[Overlap_events.png]]
- *Binding Functions to Events*
	- Delegates require a *specific function signature* for the function that we want to bind
	- We can find these signature in the *Unreal [Documentation*](https://dev.epicgames.com/documentation/en-us/unreal-engine/cpp-only-example?application_version=5.5)
	- copy the Function signature for `OnOverlapBegin`
	- Paste the Function signature in `TriggerComponent.h` file
	- Remove the `class` keywords from the functions
	- Define the functions in `TriggerComponent.cpp` file
	- in `TriggerComponent.cpp` file
		- `OnComponentBeginOverlap` : the name of the Delegate
			- `OnComponentBeginOverlap.AddDynamic(this, &UTriggerComponent::OnOverlapBegin);`
			- `OnComponentEndOverlap.AddDynamic(this, &UTriggerComponent::OnOverlapEnd);`
		- Make the Overlap begin and end delegates optional
			- Create a UProperty Member variable in `.h` file
				- `bool IsPressurePlate = false;`
			- in `.cpp` file
			- Call the Delegate in the `BeginPlay()` within the `if(IsPressurePlate) {---}`

**Tag System**

- *Tag :* a string of text which can be attached to an actor  
- `MyStuff > PlayerCharacter > Viewport`
	- `Details > Actor >> Advanced >> Tags` 
	- add a tag for actor : `PressurePlateActivator`
- in `TriggerComponent.cpp`
	- Before the if condition in both `OnOverlapBegin` **OnOverlapEnd** function
	- `OtherActor->ActorHasTag("PressurePlateActivator");`

**Logical AND Operators &&**

**Code Refactoring**

- in `TriggerComponent.h` file
	- Create a UProperty Member Variable `IsTriggered`
		- `UPROPERTY(VisibleAnywhere) bool IsTriggered = false;`
	- Create a Member function `Trigger` 
		- `void Trigger(bool NewTriggerValue);`
- in `TriggerComponent.cpp` file
	- Define the `Trigger()` function 
	- Call the Trigger() function inside the `OnOverlapBegin` and `OnOverlapEnd` functions

**Private Specifiers**

- *Access Modifiers*
	- C++ access modifiers are `public`, `private` and `protected`
	- Access Modifiers are used to assign accessibility to Class members
	- *Public modifier*
		- Class members are available everywhere. Functions outside of the class can access class members
	- *Private modifier*
		- Members cannot be access from outside functions. Only Available in the class.

Start From `03:17:02` (**REVISIT**)

- ....
- ....
- .... revisit ...

- *How Many actors are on Pressure plate*
	- Deactivate when all the actors are off the pressure plate
	- *Activator Count*
		- actor on : +1
		- actor off : -1
	- `TriggerComponent.h` file
		- VisibleAnywhere Uproperty variable :
		   `int32 ActivatorCount = 0;`
		    *int32 guarantees 32 bit* 
	-  `TriggerComponent.cpp` file
		- Call `ActivatorCount` inside the `overlapbegin` and `overlapend` functions 
			- `OverlapBegins` : `ActivatorCount++`
			- `OverlapEnds` : `ActivatorCount--`
		- for `OnOverlapEnd`
			- `if (IsTriggered && ActivatorCount == 0) {---}`
				- `Trigger(false);`


**Pressure Plate Puzzles**

- Create a new Actor BP : `BP_PressurePlate`
- Add `Trigger` component
- From settings *Enable* `IsPressurePlate`
- Place the `BP_PressurePlate` in the Test level
	- `Trigger > TriggerComponent > MoverActor > Room1_Door_Shape`
- 
~~Start From `03:32:16`~~

**Puzzle Game**

- *Action Plan* :
	- Create a `Tag` in *C++*
	- Have *Collectable* items 
	- Create a *Lock* Actor with Trigger component 
- **Create a Collectable Item**
	- Create a C++ class `CollectableItem` using *Actor* as Parent  
	- in `CollectableItem.h` file : 
		- add a UProperty Member Variable `ItemName`
	- In `Collectable.cpp` file : 
		- Create a Tag for collectable items in the game 
		- in `ACollectableItem() {---}`
			- `Tag` *(a Member variable)*
			- Tag variable can hold multiple strings of text
			- `Tag.Add("CollectableItem")`
	- Create a New BP class from *CollectableItem Class* named `BP_GlassStatue` 
	- Drag and drop Glass Status from `StarterContent > Props`
	- In the BP_GlassStaute details section add `GlassStatue` under `ItemName`
- **Create a Lock Actor class*
	* New C++ class `Lock` (*Actor class as parent*)
	* in `Lock.h` 
		* add the header files 
			* `#include "TriggerComponent.h"`
			* `#include "Components/StaticMeshComponent.h"`
		* Create the following Components : 
			* *UProperty(VisibleAnyWhere)*
				* `USceneComponent* RootComp;`
				* `UTriggerComponent* TriggerComp;`
				* `UStaticMeshComponent* KeyItemMesh;`
	* in `Lock.cpp`
		* ![[Screenshot 2026-03-02 184506.png]]
* Create a BP class where *Lock* as parent `BP_TestDoorLock`

~~Start from `3:56:25`~~

- **Collision**
	- *Collision Enabled* options : 
		- `No Collision` : Other objects will move just through the objects 
		- `Query Only` :  Spatial Queries like Raycast, Sweep and Overlaps but **NO** Physics Collision
		- `Physics Only` :  For Physics Simulation like Rigid body,  Constraints but **NO** Spatial Queries 
		- `Collision Enabled` : for Both Spatial Queries and Physics
	- *Object Type* options 
		- 
	- *Collision Presets* options : 
		- ![[Screenshot 2026-03-03 104339.png]]

~~Start From `04:08:00`~~
			- `BP_TestRoodLock` > *Key Item Mesh > Collision > Custom > Ignore Pawn*
			- `BP_Player` > *Capsule Component > Collision > By Default type is set as Pawn*

- **Set Visibility of a mesh from C++ for LockActor class**
	- *Action plan* : 
		- LMB collectable item to store the item in the inventory
		- LBM the Stored collectable item on the lock to trigger the Trigger component 
		- Specify the item as `KeyItem`
		- `KeyItemName` string 
		- Boolean `IsKeyPlaced`
	- 

**Interaction System**

- *Input System*
	-  









