
# ROS命令行工具

- rospack = ros+pack(age) : provides information related to ROS packages
- roscd = ros+cd : changes directory to a ROS package or stack
- rosls = ros+ls : lists files in a ROS package
- roscp = ros+cp : copies files from/to a ROS package
- rosmsg = ros+msg : provides information related to ROS message definitions
- rossrv = ros+srv : provides information related to ROS service definitions
- catkin_make : makes (compiles) a ROS package
  - rosmake = ros+make : makes (compiles) a ROS package (if you're not using a catkin workspace)

# ROS服务

ROS建立服务的server和client时，client不需要init_node

rosbag play \<bagname\>的时候，会等待两秒的时间，提醒这些topic的订阅者做好接收数据的准备。

stack >> package


Error saying "ImportError: No module named yaml"

pip install pyyaml 

https://www.edureka.co/community/36709/error-saying-importerror-no-module-named-yaml