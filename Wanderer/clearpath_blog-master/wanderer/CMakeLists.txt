cmake_minimum_required(VERSION 2.8.3)
project(beginner_tutorials)

find_package(catkin REQUIRED COMPONENTS roscpp rospy std_msgs geometry_msgs message_generation clearpath_base)

add_message_files( FILES Num.msg)
add_service_files( FILES AddTwoInts.srv)

generate_messages( DEPENDENCIES std_msgs geometry_msgs clearpath_base)

catkin_package( CATKIN_DEPENDS message_runtime roscpp rospy std_msgs geometry_msgs clearpath_base)

include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(wander src/wander.cpp)
target_link_libraries(wander ${catkin_LIBRARIES})
add_dependencies(wander wanderer_generate_messages_cpp)

