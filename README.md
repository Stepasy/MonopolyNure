1. Project architecture

	Whole project is briefly set 4 parts : 

	- Models
	Include all logic data and logic manager, are plain C# code, can be easily changed and tested, to keep core rules are correct. All in Logic folder.
		- LogicManager (singleton)
			- Board
			- Square
			- Player

		Models are data holders, anytime, when models changed data, will trigger a event to update specific views. 

	- Views
	Include 2 sub parts, one is UI objects, which has UI prefabs and C# codes:
		- UIManager (singleton)
			- EntryUI
			- RollingUI
			- PlayersUI
			- PopupUI
			- ConfirmUI

	another part is game objects, which are game prefabs and C# code.
		- PlayerGameObject
		- BoardGameObject
		- SquareGameObject

	In Views, objects and codes only take care how to display data, move sprites and dynamicly update, no logic code here, also they are input handler, to response click, touch or other user input, then pass to controller. Most are in Game and UI folders.

	- Controls
	GameManager is a controller in the middle of Models and Views, to control game's main workflow and response for events from Models and Views.

		- GameManager (singleton)
			- LogicManager
			- UIManager
			- Event handlers
			- Game controls

	GameManager can call LogicManager and UIManager's methods directly, but LogicManager and UIManager only fire event to trigger callback in GameManager, as Models and Views should not control controller.


	- Common
	Put utilities, contants and other 3rd part library code here.
		- Utilities
		- Contants
		- MiniJSON

	
2. Unity version and run

	Unity version: Unity 5.3.x
	In Unity Editor mode, please run main scene in Scenes folder.

	==== NOTE: For testing, game will over after 5000 rounds. =====
	All settings are in Common/Constants.cs


3. Unit test
	
	Using NUnit test and Editor test runner to run test case.
	Open Unity -> Window -> Editor test runner -> Run All.
	Test case code is in Editor folder.

4. Result output file

	When game over, click OK button will save result file to specific folder.


By Dima & Nikita
