# Falcon-CareUp_Grace_AI

**Falcon-CareUp_Grace_AI** is a Unity project designed for medical and hospital-related purposes. The project features an AI character, **GRACE AI**, which interacts with players by answering their questions accurately. In addition to AI interactions, each tied to specific in-game actions and points. The project is developed for  **VR**, with a primary focus on VR experiences.

## Project Description

The **Falcon-CareUp_Grace_AI** project focuses on creating a medical application that simulates a hospital environment. The standout feature of the project is **GRACE AI**, a smart assistant that provides players with accurate responses to medical or hospital-related queries. The project include  a points-based action.

## How to Go Through the Project

Follow these steps to get a clear understanding of how to navigate and use the **Falcon-CareUp_Grace_AI** project:

### 1. Understand the Actions System:

- Start by reviewing the `ActionManager` script. This script outlines the various actions that are available in the project.
- Each action is connected to points, and understanding how these actions work is crucial for the overall project.

### 2. Explore the XML File for Actions:

- The project uses an XML file named `Actions_Medicine_Mouth_Updated.xml` to manage all actions.
- You can find this file in the following path: `Assets/Resources/XML/Actions_Medicine_Mouth_Updated`.
- The XML file defines the actions, and exploring it will give you deeper insight into the project’s functionality.

### 3. Custom OpenXR Components:

- Although **OpenXR** is integrated, the project primarily relies on custom-built components rather than standard OpenXR features.
- These custom components are crucial for handling VR interactions, providing greater control and flexibility in the VR environment.

### 4. Important Scripts:

Several core scripts power the project. It’s important to understand these scripts to fully grasp the project’s architecture:
   - `PickableObject`
   - `ActionModule_ActionTrigger`
   - `ActionModule_ActionExpectant`
   - `ActionModule_ShowHideDelete`
   - `ShowHideObjects`

Take the time to review these scripts to learn how actions, objects, and AI interactions are controlled.

### PickableObject

## Overview

The `PickableObject` class is part of a Unity project designed for handling pickable objects in a virtual reality (VR) environment. This script allows players to interact with objects by picking them up, dropping them, and attaching them to mounting points. It also supports visual effects such as outlines and animations during these interactions.

## Features

- **Pick and Drop**: Players can pick up and drop objects smoothly with customizable transitions.
- **Mounting**: Objects can be attached to predefined mounting points within the scene.
- **Visual Feedback**: Objects can display different meshes for in-hand and out-of-hand states, along with outline effects.
- **Teleportation Support**: Handles teleportation of objects when dropped to specified locations.
- **Unity Events**: Provides Unity events for customizable interactions when objects are picked up or dropped.

## Usage

1. **Setup**: 
   - Attach the `PickableObject` script to any GameObject that you want to be pickable.
   - Assign meshes to `inHandMeshes` and `outHandMeshes` to control the object's appearance based on its state.
   - Set the `dropAnchor` to define where the object should drop when released.

2. **Interaction**:
   - Use the VR controller to pick up objects. The script manages the physics interactions and visual state changes.
   - Customize the pickup behavior by configuring the `pinchPickupTrigger` and `pinchMountTrigger` for additional interaction methods.

3. **Events**:
   - Utilize `onPickedUpObject` and `onFirstPickObject` to trigger any custom behaviors when objects are picked up.

4. **Outline**:
   - The script automatically generates outlines for pickable objects, which can be customized in the `GenerateOutline` method.


###  `ActionModule_ActionTrigger`

- **Purpose:** This script triggers various actions based on player input and conditions in the VR environment.
- **Key Features:**
  - Connects to an `ActionHandler` to manage actions based on player interactions.
  - Supports both left and right-hand triggers, allowing flexible control schemes.
  - Checks conditions before executing actions, ensuring that the right requirements are met.
  - Utilizes an `actionNumberLimit` to manage how many times an action can be triggered.
  - Contains methods to emit triggers and handle various action modules (e.g., animations, audio).
- **Important Functions:**
  - `ReceveTriggerAction(bool isLeftHand, TriggerHandAction tAction)`: Receives input from the player's hands and checks for confirmation.
  - `CheckTriggerConfirmation()`: Validates whether all conditions for triggering an action are met.
  - `EmitTrigger()`: Executes the action if the conditions are confirmed.
  - `AttemptTrigger()`: Tries to trigger the action based on the player's input.

###  `ActionModule_ActionExpectant`

- **Purpose:** This script manages the state of an action that is expected to occur based on certain conditions and player interactions.
- **Key Features:**
  - Tracks whether an action is currently active (`isCurrentAction`).
  - Checks if the action can be executed based on conditions defined in child components.
  - Interfaces with the `ActionHandler` to verify the validity of the action based on its type and associated objects.
- **Important Functions:**
  - `TryExecuteAction()`: Attempts to trigger any child action modules that meet the execution conditions.
  - `UpdateAction()`: Updates the state of the action based on its type and conditions.
  - `UpdateIsCurrentActionValue(bool value)`: Sets the current action state.
  - `Update()`: Continuously checks and updates the current action state based on defined conditions.
###  `ActionModule_ShowHideDelete`

- **Purpose:** This script is responsible for controlling the visibility and deletion of specified game objects within the Unity scene. It allows for dynamic interaction with objects based on player actions or other game events.

- **Key Features:**
  - Can show or hide multiple objects based on specified conditions.
  - Allows for the deletion of objects from the scene.
  - Supports a timeout feature to delay the execution of show/hide/delete actions.
  - Integrates with player object interactions, allowing the manipulation of objects currently held by the player.

- **Important Variables:**
  - `toShow` (bool): Determines whether the specified objects should be shown or hidden.
  - `toDelete` (bool): Indicates if the specified objects should be deleted from the scene.
  - `waitTime` (float): Specifies a delay before executing the show/hide/delete actions.
  - `ControlObjectName` (string): The name of the control object that dictates the action.
  - `ObjNames` (List<string>): A list of object names to be shown, hidden, or deleted.
  - `meshRenderer` (bool): Indicates whether to manipulate the MeshRenderer components of the objects.

- **Important Functions:**
  - `Update()`: Checks for a timeout and executes the action when the wait time is reached.
  - `StartTimeout()`: Initiates the timeout sequence, executing the action immediately if no wait time is set.
  - `Proceed()`: Executes the show/hide/delete actions based on the control object and specified object names.
  - `ShowHideObj(GameObject _obj)`: Manages the visibility and deletion of a specified object, including enabling or disabling its MeshRenderer if applicable.

### Usage Example:
1. Attach the `ActionModule_ShowHideDelete` script to a GameObject in your scene.
2. Configure the `toShow`, `toDelete`, `waitTime`, `ControlObjectName`, `ObjNames`, and `meshRenderer` properties in the Inspector.
3. Call `StartTimeout()` to begin the timeout sequence if needed, or the actions will execute automatically based on the wait time.

###  `ShowHideObjects`

- **Purpose:** This script manages the visibility of a list of game objects in Unity. It allows for showing, hiding, and toggling the active state of objects, facilitating dynamic UI interactions and gameplay events.

- **Key Features:**
  - Supports showing or hiding specific objects by name or all objects in the list.
  - Optionally manipulates MeshRenderer components for finer control over object visibility.
  - Integrates with a GameUIVR component to update UI highlights when objects are shown or hidden.
  - Provides utility functions to retrieve objects by name and check for the presence of specific objects in the list.

- **Important Variables:**
  - `hidenObjects` (List<GameObject>): A list of game objects that can be shown or hidden.
  - `gameUIVR` (GameUIVR): A reference to the GameUIVR component for UI updates.

- **Important Functions:**
  - `_show(string _name, bool toShow, bool meshRenderer = false)`: Shows or hides a specific object by name or all objects in the list. If `meshRenderer` is true, it manipulates the MeshRenderer components instead of just setting the active state.
  - `GetObjectByName(string _name)`: Returns the game object with the specified name from the `hidenObjects` list, or null if it doesn't exist.
  - `HasNeeded(string str)`: Checks if the specified object name exists in the `hidenObjects` list.
  - `_toggle(string _name)`: Toggles the active state of the object with the specified name in the `hidenObjects` list.

### Usage Example:
1. Attach the `ShowHideObjects` script to a GameObject in your scene.
2. Populate the `hidenObjects` list with the objects you want to control.
3. Call `_show("objectName", true)` to show an object, `_show("objectName", false)` to hide it, or `_toggle("objectName")` to switch its visibility state.
4. Use `GetObjectByName("objectName")` to retrieve an object for further manipulation or checks.
### 5. Hint UI Functionality:

- The project includes a **Hint UI** that provides guidance and information to users.
- This UI is controlled by the `Hint_Functionality` script, which handles how and when hints are displayed.

### `Hint_Functionality`

- **Purpose:** This script manages the display of hint UI elements within a Unity game. It shows hints related to the current action and allows users to interact with them via buttons. The hints can automatically hide based on specific conditions, such as hand position.

- **Key Features:**
  - Displays hints with associated images for different actions.
  - Shows and hides hints based on user interaction and hand position.
  - Updates hints dynamically when actions are completed through the `ActionManager`.
  - Provides functionality for opening and closing hints via UI buttons.

- **Important Variables:**
  - `hint_UI` (GameObject): The UI element that displays the hint.
  - `hintButton_UI` (GameObject): The UI element for the hint button.
  - `image` (Image): The image component used to display the hint sprite.
  - `totalActions` (int): Total number of actions for which hints are available.
  - `handTransform` (Transform): The transform of the hand to monitor for position changes.
  - `lowerRange` (float) / `higherRange` (float): Range values to determine when to hide the hint.
  - `openButton`, `openImage`, `closeButton`, `closeImage` (GameObject): UI elements for open and close button states.
  - `sprites` (Sprite[]): An array of sprites corresponding to each action hint.
  - `actionManager` (ActionManager): Reference to the action manager that tracks current actions.
  - `indexToHide` (int): Index of the action that, when completed, hides the hint UI.

- **Important Functions:**
  - `ShowHint()`: Activates the hint UI and updates it to show the current action's sprite.
  - `HideHint()`: Deactivates the hint UI and restores the button states.
  - `UpdateHint(int index)`: Updates the displayed hint based on the current action index and hides it if it matches the `indexToHide`.
  - `CheckToHide()`: A coroutine that checks hand position and hides the hint UI if the hand goes outside the specified range.
  - `HideHintWithButtons()`: Hides the hint and associated button UI when called.

### Usage Example:
1. Attach the `Hint_Functionality` script to a GameObject in your scene that manages hints.
2. Set up references for `hint_UI`, `hintButton_UI`, and other serialized fields in the Unity Inspector.
3. Ensure that the `ActionManager` is correctly set up to trigger the `OnActionComplete` event.
4. Call `ShowHint()` to display the hint UI when appropriate, and `HideHint()` to hide it.
5. Use the `UpdateHint(int index)` method to dynamically update the hint based on the current action.

## Features

- **GRACE AI**: A fully interactive AI character capable of answering player questions accurately.
- **Hospital Scenarios**: Realistic hospital environments and actions tied to specific points.
- **VR Compatibility**: The project is being developed for  VR, with a focus on virtual reality for enhanced immersion.

## Installation

### Prerequisites

- Unity Version: **2022.2.13f1**
- Tools: Visual Studio, Git, VR setup

### Clone the Repository
```bash
git clone https://github.com/your-username/Falcon-CareUp_Grace_AI.git
