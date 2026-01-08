- Create a Character class `BP_Character`
- Every Actor is madeup of several components
- `Default Character` :
	- `world settings > Game mode > Game mode override >> Game mode`
	- Add a new BP class `Game mode base` as *BP_Gamemode*
	- Select `world settings > Game mode > Game mode override >> BP_Gamemode`
	- then under *GameModeOverrride*
		- update `Default Pawn Class` => `BP_Character`
- Add a camera component to the `BP_Character`
- Add Movement code to the BP_Character event graph

- Adding Movement to `BP_Character`
- **Brute Force Method**
	- add `W keyboard`  in the event graph
	- add `add movement input` : this needs to be called every frame to work
	- add `get actor forward vector`
	- add `get acotr right vector`
	- ![[CharacterMovement_BruteForce.png]]
- **Elegant method**
	- Go to `Project Settings > Engine > Input > Axis Mapping` >>
		- `moveForward > w scale 1.0 > s scale -1.0`
	- ![[CharacterMovement_elegant_projectSettings.png]]![[CharacterMovement_elegant_evetnGraph.png]]

**Mouse Input**
- for mouse input : 
	- `controller pitch input`
	- `controller yaw input`
	- Mouse rotation does not impact character model
	- Select `BP_Character` parent node
		- `Details` > `Use Control Rotation Pitch` : Check
	- This will not impact the character model animation, character model will remain static
		- requires Character *Animation blueprint*
	- *Sensitivity* : Multiply Axis value with sensitivity values 
	- Create a `PlayerController` BP class
		- create a variable "*Sensitivity*"
		- Player controller remains persistent even after the player dies
		- Create functions `getSensitivity` and `setSensitivity` (pure)
		- World Settings > change playercontroller to `BP_PlayerController`
		- BP_Character > `Event Begin` node > `Get Player Controller` > `Cast to BP_PlayerController` > make it *pure*
		- `promote to vaiable` (*PCref*)
		- *PCref* > `get Sensitivity` > link to *Axis value multiplier* 
- Project Settings 
	- `Engine > Input > Axis Mapping > new axis mapping`
	- `LookAround` : `mouse X`
	- `LookUp` : `mouse Y` (Needs to set `Camera` > `Use Pawn Control Rotation`settings **Enabled**)

![[character_movement.png]]
**Step 1**
![[BP_playerController.png]]
**Step 2**
![[gameMode_bp_playerController.png]]
**Step 3**
![[BP_character_getnCastas_BP_playercontroller.png]]
**Step 4**
![[BP_character_BP_playerController_ref_link_to_mouse_movement.png]]

**Mouse sensitivity optimized :**

- Set Sensitivity from `Beginplay`
	- ![[Mouse_sentivity_optimized_from_beginPlay.png]]
- Then Calling the `Sentivity` variable to get sensitivity value for Mouse movements
	- ![[Mouse_sentivity_optimized_from_mouse_movement.png]]
- ![[Mouse_sentivity_optimized.png]]

- **Player Controller** is always created **BEFORE** the *Character* spawns