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
- **Congratulation msg**
	- `UpdateScore` > if `CurrentScore` == `MaxSocre`