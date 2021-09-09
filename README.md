# ROS2 project Exam prerequisite
#Run these commands in terminal

mkdir -p ~/ros2_exam_ws/src

cd ~/ros2_exam_ws/src

git clone https://git.fh-aachen.de/gh2597s/ros2_room_coverage_project.git

#After this step FH credentials may be required

cd ..

rosdep install -i --from-path src --rosdistro foxy -y

#Required packages for this to work

#1.Turtlebot3,  2.SLAM (binary install : sudo apt install ros-foxy-slam-toolbox), 3.Nav2 stack

colcon build

echo 'source ~/ros2_exam_ws/install/setup.bash' >> ~/.bashrc


ros2 launch turtlebot3_gazebo turtlebot3_house.launch.py

#New terminal

ros2 launch my_robot_slam localization.launch.py

#New terminal

ros2 launch my_robot_navigation robot_nav.launch.py 

#New terminal

ros2 run send_goal set_single_goal

#Now the turtlebot should plan a path to the left most corner of the room
