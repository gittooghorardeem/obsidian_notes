- Create e Enum folder in the Content Folder
- `RMB > Blueprint > Enumeration` > *MyEnum*
- Enum is a List of Values, perform login depending on this list 
- Creating a Variable in the Level Blueprint we can use MyEnum as *Data Type* 
- Internally, Enum is just a number
	- Number between 0 - 256
- `Switch` can be performed for enum *MyEnum*
	- From Switch we can show different output base on the what value we are Getting from MyEnum
	  ![[set_get_MyEnum.png]]
	- `Select` - a shortcut to use in BP instead of *Switch* . it Takes MyEnum's (only in BP but in c++ need to use *Switch*)
	- this will print *Banana* then *MNG*
	  mngo then bna (Need Exploration)