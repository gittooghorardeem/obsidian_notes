- Create a 1st person Game Template 
- Copy the Game Assets from the Game Asset project by Migrating the Folders to MyFirstFPSProject project.
- Create a BP Class in `Content > FirstPerson > Blueprints`
- Create an Actor Class `BP_Target`
- Add the *StaticMesh* asset tot he `BP_target`
- Add and Event `On Collision Hit` > `On Component Hit` node
- `On Component Hit` cast to `BP_FirstPersonProjectile` so that hit is only registered when Bullet hits the targer
- Create a *Game Mode* name `BP_GM_TargetGame`
- Game Mode `BP_GM_TargetGame` details : 
	- *Default Pawn Class* : `BP_FirstPersonCharacter`
	- *HUD* : `FirstPersonHUD`
- In the WorldSettings change 
	- `Game Mode > GameModeOverride => BP_GM_TargetGame`
- in `BP_GM_TargetGame`
	- add an event `AddScore`
	- Add a Variable `CurrentScore` (int)
		- `++` incremental
- in `BP_Target
	- add `GameMode` Cast to `BP_GM_Targetgame`
	- From `BP_GM_Targetgame` link to `AddScore` event
	- Add a variable `isHit` (bool) (false)
	- `Get isHit` link to `if/Branch`
	- `Branch false` link to `Set isHit`
		- set `IsHit` **True**
		- link to Cast to `BP_GM_TargetGame`
	- ***ANOTHER WAY***
	- `Get isHit` link to `Not Boolean`
		- `Not Boolean` links to `Branch True` then link to `set isHit`

~~Start from `56:49`~~

**Unreal Motion Graphics UI Designer (UMG)**

- *Content folder* create 
	- `User Interface > Widget Blueprint > User Widget` => `BP_WBP_Ui`
	- Add *Canvas* panel
	- Add *Text* > This adds an Option wheel to the canvas - *Anchor* 
		- Add *Top Left* - Anchor Top Left
		- Add *Top Right* - Anchor Top Right (*Example*)
		- Add *Center* - Anchor Center (*Example*)
		- Anchoring  makes the UI viewport Responsive
- `BP_GM_TargetGame` 
	- Add `Create Widget` => `BP_WBP_Ui`
	- Return Value for `BP_WBP_Ui` as `Add to Viewport`
- `BP_WBP_Ui`
	- Rename with **Score:**
	- Rename the base Text name to  `ScoreText`
		- Tag it as *Variable*
	- Event graph : 
	- Add the `ScoreText` variable
	- Link with `Set Text (Text)`
	- `Even BeginPlay` is **NOT** available for Widgets
	- Add `Event Construct` and link with `SetText(Text)` - this will run as soon as the widget gets created
	- Add a Custom Event `UpdateScore`
	- Cast to `BP_GM_TargetGame` > Get `CurrentScore` link to *In text* of `Settext`
- `BP_GM_TargetGame`
	- new Variable `UserInterface` type `Object variable` of `BP_WBP_Ui`
	- `Set UserInterface` take in return value of `Create BP_WBP_Ui Widget`
	  ![[Screenshot 2026-01-11 135812.png]]
- **Shortcut process**
	- `Create BP_WBP_Ui Widget` return value `promote to Variable` > `Set UserINterface`
- Have the word *Score* visible in front of the Score points
- `BP_WBP_Ui`
	- add `Append string` to `SetText`
	  ![[appendScore.png]]

~~Start from `1:08:38`~~

- **Clean up**
	- Remove `Get Game mode`,  `Cast to ...` and `Current Score`
	- Select custom event `UpdateScore`
	- Add an int input `CurrentScore`
	- `CurrentScore` input variable will appear in `BP_GM_TargetGame` > `UpdateScore` event node

- **Max Score**
	- `BP_GM_TargetGame`
	- Create variable `MaxScore`
	- add `All Actors of Class` event > `BP_Target` link with `BeginPlay`
	- got to `BP_WBP_Ui`
	- new input variable `MaxScore` and add two new pins for `Append`
	- return to `BP_GM_TargetGame`
	- Add `MaxScore` variable to `UpdateScore` custom Events
- **Congratulation msg** and stops the game "**Game Over**"
	- `UpdateScore` > if `CurrentScore` == `MaxSocre`
	- Create another Widget BP for end screen `WBP_EndScreen`
	- Add a **Restart** button 
	- add an `On Click` event to the button
	- link `Open Level (by Object Reference)` > `FirstPersonMap`
	- Go to `BP_BM_TargetGame`
	- After the *You Won* message, link with `Set Input mode UI Only` node
	- Link `Create WBP End Screen Widget` to `in widget to focus`
		- Link `Get PLayer Controller` to `Player Controller`
		- another link from `Get Player Controller` return value *show mouse* `Set Mouse Cursor`
		- *Check* `Show Mouse Cursor`
		- another link from `Get Player Controller` `Set ignore Move Input`
		- *Check* `New Move Input`
	- Link to `BeginPlay` evet
		- `get Player Controller` return value `Set input mode game only`

> **Summarize So far**

1. 1st created targer Blue Print `BP_Targer`
	1. Projectile Hitting the mesh
	2. If hit add Score![[BP_Target.png]] to the *Game Mode* > `BP_GM_TargetGame`
	   
	   
2. Game Mode `BP_GM_TargetGame`
	1. Gets the maximum target available in the level `Get All Actors of Class` > `BP_target`
	2. Based on the Target Count set *Max score*
	3. Add that in the user interface Widget BP `BP_WBP_Ui` and update score in `BP_WBP_Ui`> `Update Score`
	4. When target is hit then `Update Score` will compare *Current score* with *Max Score*
	5. If *Current Score* == *Max Score* player wins
	6. Stops Player movement and Restart the game

**Timer**
-  `BP_GM_TargetGame`
- `BeginPLay` >> `UpdateScore` >> `Set Timer by Event`
- `Set Timer by Event` > Custom Event `DecreaseCount`
- Create a Variable `Time`
- `Time` -- `DecreaseCount`
- `BP_WBP_Ui` > Custom Event `UpdateTime`
- Add Timer in the design and variable `TimerText`
- Add an input `NewTime` for `UpdateTime` event
-  **NEED TO GO THROUGH THE TUT VID**


> **Custom Weapon**

~~Start from : `1:43:30`~~

- `Content` > `FirstPerson` > `Blueprints` > `BP_FirstPersonCharacter`
- Create a Separate BP class for the Weapon. Delete the Weapon from the FirstPersoCharacter
- Clear Template Weapon properties from `EventGraph`
- Create a New Actor Class `BP_Rifle`
- Use the gun and scope from the template
- `BP_FirstPersonCharacter`
	- `EventBeginPLay` > ... > `Spawn Actor from Class` > `BP_Rifle`
	- `SpawnActorBP_Rifle` : `Spawn Transform` > `Arms`
	- `Arms` > `Get World Traansform`
		- Always Spawn, Ignore Collision
	- `SpawnActorBP_Rifle` > `Attach component to Component` > *Ayakashi_Sniper*
	- *Socket Name* : `GripPoint` and `Snap to Target` for all
	- **NEED TO GO THROUGH THE TUT VID**

~~Start From `2:08:54`~~

**UE physics (Chaos Physics)**

- Select **Fracture mode**
- Make the selected objects *Rotation to 0 0 0* and *Scale to 1 1 1* 
- Select a target object and Create a new *Geometry Collection* `GC_BP_Target4`
- `Uniform` and 3 layers of Fracture
- Go back to *Selection mode* and in Object details section *unCheck* `Show Bone Colors` under **General**
- Open the `GC_BP_Target4` settings
	- *Minimum Mass Clamp* = 1.0
	- *Mass as Density* = *Uncheck*
- Add force to the `BP_Bullet`
	- Add a **Force Field** to the bullet object
	- Before `Destroy Actor` node add `Spawn Actor by Class` > Class `FS_Master_Field`
	- *Location* from `Break Hit Result` to *spawn transform* for `SpawnActor FS Master Field`
	- Add `CE Trigger` (*FS Master Field has a ~1 sec delay after hit, this is to counter it*)
	- Another `Destroy Target` node for the *Force Field* 
	- Replace all the target objects with the `GC_BP_Target4`
		- Delete the exiting target object from `BP_target` view port
		- add `GeometryCollection`
		- Under `Chaos Physics > Rest Collectoon` add `GC_BP_Target4`

> **Environment**

- Follow the environment design tutorial : 
	- https://youtu.be/k-zMkzmduqI?si=wP-zLofxJi_3u21D
- From UE samples page, download Electric **Dream Environment Level Project**
- Open `Electric Dream Samples`
- 


