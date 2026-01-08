- **Polling** : Repeatedly call a certain function until a certain condition is met 
- `Set timer by Function name` node
	- will call a function with a given name
	- set the return value to a new variable `InitializationTimer`
	- Add comment `Polling for references` (`Select + C`)
	- 

- Collapse the *Validity check* nodes to a **Function** named **Initailize**
- add `InitializationTimer` to the *Initiaze* function
- add `clear and invalidate time handle` this is to stop the time
- Difference between `Delay` and `Timer` 
	- Timer is very precise


> **REVISIT REQUIRED**