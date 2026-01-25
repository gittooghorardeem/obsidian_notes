- Download Assets (*UE Marketplace*)
	- Unreal Engine Hour of Code (**Unable to find this in FAB library**)
		- Replacement *Unreal Learning Kit*

- Create following Folder tree
	- `Content > My3DPlatformer > Core > Player`
		- BP Class : `Character` -> `BP_MainCharacter`
	- add Skeletal Mesh : `SK_EpicCharacter`
	- Adjust Collision capsule Height and Radius 
- Create **GameMode**
	- Create Folder `Core > Framework`
	- Create BP : `BP_GM_My3DPlatformer`
	- Class Defaults : `Default Pawn Classs : BP_MainCharacter`
	- Go to `Project Settings > Maps & Modes`
		- Default GameMode : `BP_GM_My3DPlatformer`
- Go to `BP_MainCharacter`
	- Add `Camera` to the character
	- Add `Spring Arm` under the Camera with Root (This will prevent the Camera from getting clipped from other objects in the scene)
	- Move the `Camera` under the `Spring Arm`
		- Configure the `Spring Arm` transform values to adjust the camera view
- Implement Movement to the characer
	- Go to `Project Settings > Inputs`
		- Add `MoveForwar` : Scale 1 and -1
			- Add gamepad L Thumbstick Y-Axis Movement
		- Add `MoveRight` : Scale 1 and -1
			- Add gamepad L thumbstick X-Axis movement
		- Add `Jump` : Scale 1
			- Add gamepad Facebutton Bottom
		- Add `Turn` (mouse x-axis)
		- Add `Lookup` (mouse y-axis) : Scale : -1 (*to counteract the invert control*)

~~Start from `00:19:18`~~
 - Add Movement to the Character
 - In `BP_MainCharacter` BP
	 - Input action event `Jump`
	 - Input `MoveForward`
		 - `Add Movement input`
		 - ~~Get Character Location :`Character Movement` > `Get Last Update Location` : World Direction~~
		 - ~~world Direction : x = -1~~
		 - `Get Actor Forward Vector` : World direction
	 - Input `MoveRight` 
		 - `Add Movement Input`
		 - `Get Actor right vector` : world Direction
	- `Spring Arm` > Use Pawn Controller Rotation - `True`
	- Input `Turn`
		- `Add Controller Yaw`
	- Input `Lookup`
		- `Add Controller Pitch`
- To unlink camera rotation with character rotation 
	- `BP_MainCharacter(self)` > `Class Defaults `> `Pawn` > UNCHECK `Use Controller rotation Yaw`
- Orient the Character with the Movement direction 
	- `Character Movement` > `Character Movement (Rotation Settings)`> CHECK `Orient Rotation to Movement`

> **Create Level**

- Add Light actors
	- *DirectionalLight*
	- *SkyAtmosphere*
	- *Exponential Height Fog*
	- *SkyLight*
- Add *Volumetric Cloud*
- Add *PlayerStart*

- Configure Character Jump
	- `BP_MainCharacter` 
