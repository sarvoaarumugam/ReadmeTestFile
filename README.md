# Falcon-CareUp_Grace_AI

**Falcon-CareUp_Grace_AI** is a Unity project designed for medical and hospital-related purposes. The project features an AI character, **GRACE AI**, which interacts with players by answering their questions accurately. In addition to AI interactions, each tied to specific in-game actions and points. The project is developed for **WebGL** and **VR**, with a primary focus on VR experiences.

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
   - `ActionManager`
   - `ActionModule_ActionTrigger`
   - `ActionModule_ActionExpectant`
   - `ActionModule_ShowHideDelete`
   - `ShowHideObjects`

Take the time to review these scripts to learn how actions, objects, and AI interactions are controlled.

### 5. Hint UI Functionality:

- The project includes a **Hint UI** that provides guidance and information to users.
- This UI is controlled by the `Hint_Functionality` script, which handles how and when hints are displayed.


## Features

- **GRACE AI**: A fully interactive AI character capable of answering player questions accurately.
- **Hospital Scenarios**: Realistic hospital environments and actions tied to specific points.
- **WebGL and VR Compatibility**: The project is being developed for both WebGL and VR, with a focus on virtual reality for enhanced immersion.

## Installation

### Prerequisites

- Unity Version: **2022.2.13f1**
- Tools: Visual Studio, Git, WebGL/VR setup

### Clone the Repository
```bash
git clone https://github.com/your-username/Falcon-CareUp_Grace_AI.git
