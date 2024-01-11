For building, the command is:
`docker build -t <image-name> .`

## For running, the command is:
`docker run -it --user ros --network=host --ipc=host -v $PWD/ros2_ws:/home/ros/ros2_ws -v /tmp/.X11-unix:/tmp/.X11-unix:rw -env=DISPLAY ros_image`

# Explanation of the arguments:
`--network=host`: This allows the container to use the host network stack. This is required for the container to be able to communicate with the ROS master running on the host machine.
`--ipc=host`: This allows the container to use the host IPC stack. This is required for the container to be able to communicate with the ROS master running on the host machine.
`-v $PWD/ros2_ws:/home/ros/ros2_ws`: This mounts the ROS2 workspace on the host machine to the ROS2 workspace in the container. This allows the container to access the ROS2 workspace on the host machine.

(if you're running a desktop version and need access to the display e.g. for rviz2 etc):
`-v /tmp/.X11-unix:/tmp/.X11-unix:rw`: This mounts the X11 socket on the host machine to the X11 socket in the container. This allows the container to display GUIs on the host machine.
`--env=DISPLAY:` This sets the DISPLAY environment variable in the container to the value of the DISPLAY environment variable on the host machine. This allows the container to display GUIs on the host machine.

