# ROS 2 Turtlesim - Catch the Turtle

A beginner ROS 2 project built with Python on **Jazzy** using the turtlesim simulator.

Two nodes work together — one keeps spawning turtles at random positions, and the other makes `turtle1` automatically chase and catch the nearest one.



## What I learnt building this

- Creating ROS 2 nodes in Python
- Using **topics** (publisher / subscriber) to share data between nodes
- Using **services** to spawn and kill turtles
- Computing the closest turtle using distance math and driving toward it with velocity commands



## Nodes

**`turtle_spawner`** — periodically calls the `/spawn` service to add new turtles, then publishes their names on a topic so the controller knows who's alive.

**`turtle_controller`** — subscribes to that topic and to `turtle1`'s pose, finds the nearest turtle, and publishes velocity commands to `/turtle1/cmd_vel` to catch it. Once caught, it calls `/kill` to remove that turtle.



## How to run

```bash
# Terminal 1
ros2 run turtlesim turtlesim_node

# Terminal 2
ros2 run my_robot_bringup turtle_spawner

# Terminal 3
ros2 run my_robot_bringup turtle_controller
```

Or run simply using the launch file provided, which will run all the above three nodes (manually).


## Built with

- ROS 2 Jazzy
- Python (`rclpy`)
- turtlesim
