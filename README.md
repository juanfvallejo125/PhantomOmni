UNMAINTAINED
============

This repo is no longer maintained. You should fork it if you wish to make contributions.

phantom_omni
============

ROS Node for Sensable Phantom Omni devices

Requires the [omni_description](https://github.com/danepowell/omni_description) package. 

Parameters:
- ~omni_name (default: omni1)

Publishes:
- OMNI_NAME_joint_states (sensor_msgs/JointState): The state of each of the omni's joints.
- OMNI_NAME_button (phantom_omni/PhantomButtonEvent): Events for the grey and white buttons.

Subscribes:
- OMNI_NAME_force_feedback (phantom_omni/OmniFeedback): Force feedback to be displayed on the omni. Takes a force and a position. If you simultaneously click the grey and white buttons, the omni will 'lock' to the position.

This is based on the [original phantom_omni package](http://www.ros.org/wiki/phantom_omni). However, it has several advantages:
- Catkinized build system
- Compatibility with ROS Groovy
- Uses URDF description of Omni and the robot_state_publisher instead of hardcoded transforms.
- Improved auto-calibration
- Streamlined code / organization / bug fixes.
- Defaults to gravity compensation mode (instead of locking to the 'zero' position).

To see it in action, simply:
roslaunch phantom_omni omni.launch

## Edits and Comments for ARM LAB by Juan Vallejo
* Installation instructions
  * Install the drivers and the OpenHaptics SDK
  * Execute Geomagic_Touch_Setup in /opt/geomagic_touch_device_driver
  * Select the Geomagic Touch and add a new device. Name the device Phantom Omni
  * Click Apply
  * Compile the catkin workspace with both the phantom_omni and omni_description (https://github.com/danepowell/omni_description) packages in it
* Edits made to this package
  * Added the parameter omni_name in omni.launch to setup the name of the omni in the published topics
  * Changed onmni.cpp to initialize the omni device named Phantom Omni
  * The velocity of the 3 first joints in joint_states is the cartesian velocity (Experimental)
