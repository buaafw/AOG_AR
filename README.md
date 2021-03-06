# AOG_AR

### Code for ICRA 2017 paper - Interactive Robot Knowledge Patching using Augmented Reality

### ROS Package : send_to_hololens/

#### Library Used
* [tacopie](https://github.com/Cylix/tacopie)
* [OpenBottle/robot_control](https://github.com/xiaozhuchacha/OpenBottle/tree/master/robot_control) for controlling a rethink baxter robot

#### source files 
##### TCPPackageConstants.h
Defines constants for the format of the packets transmitted between ROS and Hololens.

##### send_to_hololens.cpp
Establishes TCP connection with Hololens. Listens to different types of ROS messages (TF, image etc.) , and does some processing specific to the robot(Baxter) and gripper used in this application. Send updates on robot states to Hololens, and also listens to commands and updates sent by user from Hololens.

### Unity Application : Assets/ 	 ProjectSettings/

#### Development Platform 
* Microsoft Hololens
* Unity 5.6
* Visual Studio 2017

#### Library Used
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [HoloLensARToolKit](https://github.com/qian256/HoloLensARToolKit)

#### Overview
This application receives real-time updates on robot states(e.g. TF, kinect images, gripper force) from ROS, and displays those information as hololens to users through Microsoft Hololens platform. The user can also see the knowledge base of the robot represented as an and-or graph, and interactively patch the knowledge structure. 


#### Scripts
##### TCPManager.cs
Listens for a TCP connection first. Once connection established, try to fetch data every frame, and stores them in the buffer for other scripts to access.

##### SensorDisplay.cs
Controls the visibility and position of the holograms and the buttons. Convert data from the frame of the robot to world frame of the Hololens application.

##### Node.cs
Class to represent a node in the and-or graph.

##### SimpleTree.cs
Class to represent the and-or graph structure. Provide function to go to the next end node(action) from any end node.

##### SlotPanel.cs, Slot.cs, NodeChange.cs, DragHandler.cs, Inventory.cs
Implements drag and drop on canvas to enable and-or graph patching. Parse the and-or graph to generate action sequence.

##### OnScreenKeyboard.cs
Helper class to use TouchScreenKeyboard class to edit new action name. (Requires building in XMAL instead of D3D)

##### HandDraggableCustom.cs, GripperNewPoseControl.cs, EditAction.cs
Allow user to edit an end node, and set new pose for the action by dragging a gripper hologram with hand gesture.

### Wiki
https://github.com/xiaozhuchacha/AOG_AR/wiki
