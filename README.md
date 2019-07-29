# MRG_Racecar_App
An app that can teleoperate a racecar or serve as a joy controller for ROS purposes

# How to use
1. Get rosbridge on your robot
2. Open a command terminal and type: 
```
roslaunch rosbridge_server rosbridge_websocket.launch
```
3. Make sure your phone and your robot are connected to the same wifi
4. Open the app
5. Click on the host button. Input the IP Adress of your wifi followed by a colon and the port rosbridge is connected to. The default port rosbridge connects to is 9090, which you can edit in the launch file. Below is an example:
128.31.38.17:9090
6. If the connect button turns green, then you're in. Otherwise, something is wrong with the connection.
