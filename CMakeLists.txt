cmake_minimum_required(VERSION 3.0.2)
project(drone_planner)

set(CMAKE_CXX_STANDARD 17)

find_package(catkin REQUIRED COMPONENTS
	roscpp
	std_msgs
	geometry_msgs
	mrs_msgs
	message_generation
)

generate_messages(
	DEPENDENCIES
		std_msgs
		geometry_msgs
)

catkin_package(
	CATKIN_DEPENDS message_runtime
)

add_executable(planner src/main.cpp)

target_link_libraries(planner
	PRIVATE
		${catkin_LIBRARIES}
)

target_include_directories(planner
	PRIVATE
		${catkin_INCLUDE_DIRS}
)
