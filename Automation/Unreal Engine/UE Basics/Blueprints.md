- Open *Level Blueprint*
- "*BeginPlay*" - as soon as you load the game
- in the blueprint editor, any selected object can be referenced by a new node (`RMB` options)
- **Pure Function** : 
	- whenever needs to return immediate value 
	- value is not cached, each time it is called
	- shows in `green`
- **Event Tick** : 
	- a function that is called on every frame


> **Variables**

- ***vector** types are a **struct***
- `Clrt + Hold + Drag` => get value
- `Alt + Hold + Drag` => set value

> **Structures / Structs**

- `Content Browser > RMB > Blueprints > Stucture` 
- **Structs** : Wrap a bunch of data and methods (in general)
	- **In Blueprints :**
		- *a collection of Variables* 
		- cannot have Functions for structs 
		- In short *i variable stores multiple variables in it*
- `SetMembers in <MyStucture>` to set values to the in the level design 

> **Enumeration**

- `Content Browser > RMB > Blueprints > Enumeration` 
- **Enum** : 
- Enum - Drag - can be associated with a switch 
- *Need to to follow the video guide*

> **Functions**

- *Need to to follow the video guide*
- No **Delay** available 

> **Macros**

- **Delay** can be added in macros


> **MISC**

- **Sequence** node can be add between the nodes to provide sequentially run multiple nodes

> **Collapsed Graphs**

- 1:08:43
- *Functions* can be called from multiple *blueprints*
- *Macros* **CAN NOT** be called for multiple *blueprints* 
- *Collapsed Graph* - groups multiple nodes

> **Branching**

- 11:12:11
- 
