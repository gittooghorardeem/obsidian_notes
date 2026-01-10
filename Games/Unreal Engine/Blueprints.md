- Blueprint basically a visual scripting language 
- `level Blueprint` : Level Blueprint 
	- `Open Level Blueprint`
	- `Event BeginPlay` : When load a Level
	- `Event Tick` : Calls on every frame
- Any actor placed on the level map, will have a reference pointer in the `RMB` option in the Level Blueprint editor.
	- `Get Actor Location` : 
		- a *Pure Function*
			- A function to return immediate values
			- 
		- So no Execution pin
		- Gets the Live location of the Actor
	- `Set Actor Location`
	- `+` : after dragging a link will place a summation/increment node 
	  ![[BP_spotLight_move.png]]
	- `White triangles` : Execution Pins, Only *Left -> Right*
	- ![[split_struct_pin.png]]![[split_struct_pin_expanded.png]]
- If can add <= or >= then node by just searching `<=` or `>=`
- Data type can be changed by `RMB` on the data type input pins

> **Event Graphs**

- Move the Character BP to the top tool bar
	- Press Play
	- move the game view to a side
	- Game interactions will highlighted in the character BP in real time (THIS IS SOOOO COOL!!!!)
- **Red Nodes** : Events
	- can be linked to other BPs
	- 
- 