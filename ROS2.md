# ROS

## 0. Check executable instructions

- `ros2 pkg executables <pkg_name>`

## 1. Topics

<img src="http://docs.ros.org/en/humble/_images/Topic-MultiplePublisherandMultipleSubscriber.gif" style="zoom: 100%" />

- Visualizing nodes and services: `rqt_graph`

- See topic list: `ros2 topic list` ->see types: `ros2 topic list -t`

- See data published on a topic: `ros2 topic echo <topic_name>`

- See topic type, # of publisher, # of subscription: `ros2 topic info <topic_name>`

- See message transmitted through nodes: `ros2 interface show <topic_name>`

- Publish data to a topic: `ros2 topic pub <topic_name> <msg_type> '<args>'`

  - If once: `ros2 topic pub --once <topic_name> <msg_type> '<args>'`
  - If at x Hz: `ros2 topic pub --rate x <topic_name> <msg_type> '<args>'`

- See rate of data: `ros2 topic hz <topic_name>`

## 2. Services

<img src="http://docs.ros.org/en/humble/_images/Service-MultipleServiceClient.gif" style="zoom: 100%" />

- See service list: `ros2 service list`

- See service type: `ros2 service type <service_name>`

- Combining service list and type:`ros2 service list -t`

- Find all services of the **type**: `ros2 service find <type_name>`

- See request format of a service type: `ros2 interface show <type_name>`

- Call a service: `ros2 service call <service_name> <service_type> <arguments>` (`<arguments>` optional)

  *eg*. `ros2 service call /spawn turtlesim/srv/Spawn "{x: 2, y: 2, theta: 0.2, name: ''}"`

  ## 3. Parameters

- See parameters: `ros2 param list`
- Get value of a parameter: `ros2 param get <node_name> <parameter_name>`
- Set value of a parameter: `ros2 param set <node_name> <parameter_name> <value>`
- See all values of parameters in the node: `ros2 param dump <node_name>`
  - Save the values in a file: `ros2 param dump <node_name> > turtlesim.yaml`
- Load parameters from a file: `ros2 param load <node_name> <parameter_file>`
  - Load parameters on node startup: `ros2 run <package_name> <executable_name> --ros-args --params-file <file_name>`

## 4. Actions

<img src="http://docs.ros.org/en/humble/_images/Action-SingleActionClient.gif" style="zoom: 100%" />

- See node information: `ros2 node info <node_name>`

- See action list: `ros2 action list`
  - With type: `ros2 action list -t`

- See action info: `ros2 action info <action_name>`

- See format transmitted in action: `ros2 interface show <action_name>`

  returned in the following structure:

  | Goal request |
  | :----------: |
  |  **Result**  |
  | **Feedback** |

  

- Send a goal: `ros2 action send_goal <action_name> <action_type> <values>`

  - with feedback shown: `ros2 action send_goal <action_name> <action_type> <values> --feedback`

    

## 5. rqt_console

`ros2 run rqt_console rqt_console`

setting default logger level: `ros2 run <pkg_name> <node name> --ros-args --log-level WARN`

## 6. Recording and playing back data with `ros bag`

- Start recording: `ros2 bag record -o <bag_file_name> <topic_name> <topic_name> ...`

- Details of recording: `ros2 bag info <bag_file_name>`

- Play recording: `ros2 bag play <bag_file_name>`

## 7. Creating a workspace

- Create a folder

- Build packages using colcon: `colcon build`

- Source the overlay: 1.`source /opt/ros/humble/setup.bash` 2. in the workspace: `. install/local_setup.bash`

## 8. Creating a package

- Creating a package: `ros2 pkg create --build-type ament_cmake <pkg_name>`

