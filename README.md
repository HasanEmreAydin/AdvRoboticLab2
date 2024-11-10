# AdvRoboticLab2

# TurtleBot Advanced Explorer

This project is a simple ROS (Robot Operating System) node for controlling a TurtleBot. The node subscribes to the LaserScan topic and uses the data to control the TurtleBot's movements, helping it avoid obstacles.

## Features
- Detects obstacles within a specified distance threshold.
- Moves forward when no obstacle is detected.
- Performs a random turn if an obstacle is detected directly ahead.
- Uses ROS to publish velocity commands to the `/cmd_vel` topic.

## Prerequisites
- **ROS** (Robot Operating System) installed.
- **TurtleBot** with a laser scanner or a similar robot setup.

## Installation
1. Clone the repository and navigate to the project directory:
    ```bash
    git clone <repository_link>
    cd turtlebot_advanced_explorer
    ```

2. Build the ROS package:
    ```bash
    catkin_make
    ```

3. Source the ROS setup file:
    ```bash
    source devel/setup.bash
    ```

## Usage
1. Launch your TurtleBot and make sure the laser scanner topic (`/scan`) is active.

2. Run the `turtlebot_advanced_explorer` node:
    ```bash
    rosrun turtlebot_advanced_explorer turtlebot_advanced_explorer
    ```

## Code Explanation
- **Obstacle Detection**: The `scanCallback` function processes laser scan data to detect obstacles within a 20 cm range from the center of the robot's field of view.
- **Movement Control**: 
  - If an obstacle is detected, the robot slows down and turns randomly.
  - If no obstacle is detected, the robot moves forward at a normal speed.

## Parameters
- `obstacle_distance_threshold`: The distance threshold (in meters) to detect obstacles. Set to 0.2 meters (20 cm) by default.

## Example Output
The node publishes `geometry_msgs/Twist` messages to the `/cmd_vel` topic, causing the TurtleBot to move or turn based on the obstacle detection logic.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
