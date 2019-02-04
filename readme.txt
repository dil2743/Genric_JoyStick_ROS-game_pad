ROS driver for a generic Linux joystick. 
The joy package contains joy_node, a node that interfaces a generic Linux joystick to ROS. 
This node publishes a "Joy" message, which contains the current state of each one of the joystick's buttons and axes.
Supported Hardware
This node should work with any joystick that is supported by Linux.

API Stability
The ROS API of this node should be considered stable.

Official Documentation

Nodes
joy_node.py 
The joy_node provides a generic Linux joystick node.

Published
joy 
sensor_msgs/Joy 
Outputs the joystick state.

Parameters
~dev 
type = string 
default = /dev/input/js0 
Linux joystick device from which to read joystick events.

~deadzone 
type = double 
default = 0.05 
Amount by which the joystick has to move before it is considered to be off-center. This parameter is specified relative to an axis normalized between -1 and 1. Thus, 0.1 means that the joystick has to move 10% of the way to the edge of an axis's range before that axis will output a non-zero value. Linux does its own deadzone processing, so in many cases this value can be set to zero.

~autorepeat_rate 
type = double 
default = 0.0 (disabled) 
Rate in Hz at which a joystick that has a non-changing state will resend the previously sent message.

~coalesce_interval 
type = double 
default = 0.001 
Axis events that are received within coalesce_interval (seconds) of each other are sent out in a single ROS message. Since the kernel sends each axis motion as a separate event, coalescing greatly reduces the rate at which messages are sent. This option can also be used to limit the rate of outgoing messages. Button events are always sent out immediately to avoid missing button presses.

Using this Package
For an example of using joy_node to control a teleoperation node with a joystick, see the tutorials.

In some cases, multiple joysticks may control a single robot. For example, a user may use the default joystick to drive a robot, but a second user may wish to use a different kind. Since the button mappings on each joystick may be different, it will be necessary to remap buttons on one joystick so they can match. See the Joystick Remapper package for details.

Application
Microsoft Xbox 360 Wireless Controller for Windows
Table of index number of /joy.buttons:
