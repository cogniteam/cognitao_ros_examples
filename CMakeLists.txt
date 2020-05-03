cmake_minimum_required(VERSION 2.8.3)

project(cognitao_ros_examples)

add_compile_options(-std=c++14)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  actionlib_msgs
  dynamic_reconfigure
  message_generation
  actionlib 
  genmsg
  actionlib_msgs   
  cognitao_ros
)

find_package(Threads)

include_directories(
	include
	${catkin_INCLUDE_DIRS} 
)


catkin_package()

#
# Build
#



#
# Action server executable example
#

add_executable(action_wait_server 
src/main.cpp
src/RosActionWaitServer.cpp
)


add_dependencies(action_wait_server
${${PROJECT_NAME}_EXPORTED_TARGETS}
${catkin_EXPORTED_TARGETS}
)

target_link_libraries(action_wait_server
cognitao_core
${catkin_LIBRARIES}	
)

