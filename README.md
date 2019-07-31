# MRG_Racecar_App
An app that can teleoperate a racecar or serve as a joy controller for ROS purposes. It publishes joy messages and string messages and also recieves Int32 messages. The joy messages published are based off the Logitech Wireless Gamepad F710 (DirectInput Mode).

# Requirements
* Swift 4
* iOS 8+
* ROSbridge

# Installation (For Mac)
1. Clone the repository
2. Go to the project's directory and type:
```
pod install
```

# How to use
1. Get [rosbridge](https://github.com/RobotWebTools/rosbridge_suite) on your robot by cloning the rosbridge repository
2. Open a command terminal and type: 
```
roslaunch rosbridge_server rosbridge_websocket.launch
```
3. Make sure your phone and your robot are connected to the same wifi
4. Open the app
5. Click on the host button. Input the IP Adress of your wifi followed by a colon and the port rosbridge is connected to. The default port rosbridge connects to is 9090, which you can edit in the launch file. Below is an example:
123.45.67.89:9090
6. If the connect button turns red, then you've successfully established connection. Otherwise, something is wrong with the connection. If it fails with the following error:
```
Problem of md5sum warning when web is refreshed 
```
Comment out lines 321-325 in [rosbridge_library/pulibhser.py](https://github.com/RobotWebTools/rosbridge_suite/blob/develop/rosbridge_library/src/rosbridge_library/internal/publishers.py):
```
    def _unregister_impl(self, topic):
        if not self._publishers[topic].has_clients():
            self._publishers[topic].unregister()
            del self._publishers[topic]
        del self.unregister_timers[topic]
```
More info can be found here: https://github.com/RobotWebTools/rosbridge_suite/issues/138
7. To actually use the app, you will have to launch the file you use for your robot
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

# Detecting April Tags
This app subscribes to a topic with the Int32 message type. It is used to generate a log of april tags, which can be viewed in the april tags tab. More information on April Tags here: https://april.eecs.umich.edu/software/apriltag.html

# Changing topics to publish 
You can change topics to publish from the 'Publishers and Subscribers' tab. However, this can only be done when you are disconnected from your robot. As of now, you will have to manually input the topics you want every time you quit and reopen the app.

# Toggle buttons
On the robot controller screen, you can toggle between 'Off', 'Teleop' and 'Auto'. They publish the following joy.button messages:
1. Off:    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
2. Teleop: [0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0]
3. Auto:   [0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0]

# Author
Brandon Man, brandonkingyiuman@gmail.com
Research intern at MIT CSAIL, student at Cate School, CA

# Acknowledgements
I used [RBS Manager](https://github.com/wesgood/RBSManager) for this project. Thanks goes to @wesgood for creating RBS Manager.

# License
The MRG Racecar App is available under the MIT license. See the LICENSE file for more info.

