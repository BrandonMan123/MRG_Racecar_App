# MRG_Racecar_App
An app that can teleoperate a racecar or serve as a joy controller for ROS purposes

# Requirements
* Swift 4
* iOS 8+
* ROSbridge

# How to use
1. Get [rosbridge](https://github.com/RobotWebTools/rosbridge_suite) on your robot
2. Open a command terminal and type: 
```
roslaunch rosbridge_server rosbridge_websocket.launch
```
3. Make sure your phone and your robot are connected to the same wifi
4. Open the app
5. Click on the host button. Input the IP Adress of your wifi followed by a colon and the port rosbridge is connected to. The default port rosbridge connects to is 9090, which you can edit in the launch file. Below is an example:
128.31.38.17:9090
6. If the connect button turns green, then you've successfully established connection. Otherwise, something is wrong with the connection.

# Messages published
The app publishes [joy messages](https://wiki.ros.org/joy) and string messages and also recieves Int32 messages. The app has three publishers total, each having a different function.
 * Racecar publisher
   - It publishes joy messages to your robot. The joy messages published can be accessed via viewController.swift
   - The direction pad will be upgraded to a joystick
 
 * Debug publisher
   - If your robot doesn't move after being connected, this publisher publishes strings indicating what directional buttons were pressed:
   - Up button: "Up button pressed"
   - Down button: "Down button pressed"
   - Left button: "Left button pressed"
   - Right button: "Right button pressed"

* April Tag publisher
  - Sends string messages to the april tag topic. It can be used for any purpose. It publishes messages when the publish message is clicked on the controller screen.


