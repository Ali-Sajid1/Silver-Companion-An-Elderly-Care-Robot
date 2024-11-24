# Silver-Companion-An-Elderly-Care-Robot

**More About Silver Companion:**

**Synopsis:**

In East Asian Countries like Japan and China, 1/3rd of the total population consists of elderly individuals. Shockingly, up to 45% of them experience total social isolation, resulting in profound neuropsychological and societal challenges such as depression, loneliness, and tragic spikes in the suicide rates. Silver Companion Robot is a beacon of hope, driven by robotics and designed with user-centered design principles. With personalized care and stead-fast companionship, it offers intuitive features like voice interaction, robot-face expressions with complementing micro-gestures, and seamless navigation. Silver Companion Robot aims at fostering the well-being of elders, uplifting their quality of life, and promoting meaningful connections, making their every moment vibrant, fulfilling, and alleviating the feelings of isolation.


**Graphical Abstract:**

![image](https://github.com/user-attachments/assets/224d28e3-3b83-44e4-afcc-fd2f7df529a9)


**A. Technical Specifications**


_**A.1. Kobuki Base**_

Dimensions: 306mm (L) x 332mm (W) x 140mm (H)

Weight: 3.5kg

Battery: 14.8V Li-ion, 2.2Ah

Max Speed: 0.7m/s

Payload: 5kg

Sensors: Cliff sensors, bump sensors, wheel drop sensors, encoder sensors, gyro sensor

Connectivity: USB, UART, GPIO, Analog input

Run Time: Approx. 2 hours

Charging Time: Approx. 3 hours


_**A.2. Jetson Nano Developer Kit**_

Processor: Quad-core ARM Cortex-A57 CPU

GPU: 128-core Maxwell GPU

Memory: 4GB LPDDR4

Storage: microSD (card not included)

Connectivity: Gigabit Ethernet, M.2 Key E

USB Ports: 4x USB 3.0, 1x USB 2.0 Micro-B

Display: HDMI and DisplayPort

Power: 5V⎓4A DC

Operating System: Linux (NVIDIA JetPack)

Dimensions: 100mm x 80mm x 29mm


_**A.3. Intel RealSense Depth Camera D435i**_

Depth Technology: Stereo

Depth Field of View (FOV): 86° x 57°

Depth Output Resolution: Up to 1280 x 720

Depth Frame Rate: Up to 90 fps

RGB Sensor Resolution: 1920 x 1080

RGB Frame Rate: 30 fps

IMU: 6 Degrees of Freedom (6DoF)

Connectors: USB 3.1 Gen 1

Power Consumption: 1.5W

Dimensions: 90mm x 25mm x 25mm


_**A.4. Servo Motor Driver Module PCA9685**_

PWM Channels: 16-channel, 12-bit PWM outputs

Control Interface: I2C interface with selectable addresses

Output Enable: Configurable push-pull or open-drain output

Frequency: Adjustable frequency PWM up to 1.6 kHz

Operating Voltage: 2.3V to 5.5V

Maximum Output Current: 25mA per channel

Dimensions: 25mm x 25mm

Operating Temperature Range: -40°C to +85°C


_**A.5. RC Geared Servo Motor MG996R**_

Operating Voltage: 4.8V to 7.2V

Stall Torque: 9.4 kgf·cm (4.8V), 11 kgf·cm (6V)

Operating Speed: 0.19 sec/60° (4.8V), 0.14 sec/60° (6V)

Dimensions: 40.7mm x 19.7mm x 42.9mm

Weight: 55g

Gear Type: Metal gears

Connector Wire Length: 300mm

Temperature Range: -30°C to +60°C


**B. Circuit Diagram**

![image](https://github.com/user-attachments/assets/9f3f6d48-75bd-4005-904f-92e0d69bb20f)


_**Legend:**_

P: Power to Jetson

M: Power to servo motor driver

Wires

Red: +V

Black: Gnd

Yellow: Signal

L.Blue: Universal Serial Bus

HDMI: Green

D.Blue: Audio


**C. ROS Architecture Nodal Maps**


**C.1. Representing all Publisher Nodes, Subscriber Nodes, and their Interconnectivity**

![rosgraph_all_nodes](https://github.com/user-attachments/assets/be21466d-e198-4de3-a17f-e72a3dfb878d)


**C.2. Representing all ROS Topics**

![rosgraph_all_topics](https://github.com/user-attachments/assets/a2004187-3e69-45a9-8a1d-efd74b31b2a6)


**C.3. RRepresenting all Active Topics**

![rosgraph_active_topics](https://github.com/user-attachments/assets/7f249c6b-1ebc-4ee3-b8dc-bdd58cda778c)


**D. Instructions for Starting with ROS and Kobuki**


**D.1. Starting with ROS and Jetson Nano**


_**Step 0:**_

1. Learn ROS Basics (https://drive.google.com/drive/folders/1y7Py9Ga5A90boky8_vE4ajJmdcy-uvBy)

2. Learn Jetson Nano Basics (https://www.youtube.com/watch?v=5INy0FvaWLw)


_**Step 1:**_

1. Install ROS Melodic (https://wiki.ros.org/melodic/Installation/Ubuntu)

2. Create a new workspace directory

3. Run catkin_make


_**Step 2:**_

1. Install Turtlebot2 package (https://www.youtube.com/watch?v=rniyH8dY5t4)

2. Run catkin_make (may encounter cmake error regarding opencv – image_geometry issue)

3. Correct the opencv – image_geometry issue (https://jstar0525.tistory.com/306)

4. Run catkin_make (may encounter cmake error regarding opencv – cv_bridge issue)

5. Correct the opencv – cv_bridge issue (https://jstar0525.tistory.com/118)

6. Run catkin_make (may encounter cmake error regarding turtlebot_kobuki joystick)

7. Correct the turtlebot_kobuki joystick issue by typing sudo apt-get install ros-melodic-joy*


_**Step 3:**_ 

Make ROS Melodic use Python3 for code execution (https://gist.github.com/azidanit/9950aa5408acdbe25f0ec431654da8d6) including #!/usr/bin/env python


**D.2. Starting with Kobuki with ROS Melodic**


Learn Turtlebot on ROS: Refer to the TurtleBot learning platform for comprehensive tutorials and resources: https://learn.turtlebot.com/


_**SSH Setup for PC:**_

1. Install SSH server: sudo apt-get install openssh-server

2. Check SSH status: sudo service ssh status

3. Connect to localhost: ssh localhost

_**Know the IP Address of Kobuki:**_

1. Check IP address: ifconfig

_**Get into the Kobuki’s Server:**_

1. Connect to Kobuki: ssh turtlebot@[ip_of_turtlebot]

_**Connect the Kobuki Base with the Laptop:**_

1. Connect to Kobuki: ssh turtlebot@[ip_of_turtlebot]

2. Launch Kobuki: roslaunch turtlebot_bringup minimal.launch


_**Control the Kobuki from PC:**_

1. Launch teleoperation: roslaunch turtlebot_teleop keyboard_teleop.launch

_**Setup Depth Camera as Default 3D Scanner of Kobuki:**_

1. Check current 3D sensor: echo $TURTLEBOT_3D_SENSOR

2. Set default sensor: echo "export TURTLEBOT_3D_SENSOR=<name of scanner>" >>.bashrc


**SLAM Implementation:**


**Mapping:**

_**On Turtlebot:**_

1. Launch Turtlebot: roslaunch turtlebot_bringup minimal.launch

2. Launch Gmapping: roslaunch turtlebot_navigation gmapping_demo.launch

_**On PC:**_

1. Launch RViz for visualization: roslaunch turtlebot_rviz_launchers view_navigation.launch

2. Launch teleoperation: roslaunch turtlebot_teleop keyboard_teleop.launch

_**Save the Map:**_

1. Save map: rosrun map_server map_saver -f $HOME/my_map
 

**Localization:**

_**On Turtlebot:**_

1. Launch Turtlebot: roslaunch turtlebot_bringup minimal.launch

2. Launch AMCL for localization: roslaunch turtlebot_navigation amcl_demo.launch map_file:=/home/ccr/my_map.yaml

_**On PC:**_

1. Launch RViz for visualization: roslaunch turtlebot_rviz_launchers view_navigation.launch --
screen
