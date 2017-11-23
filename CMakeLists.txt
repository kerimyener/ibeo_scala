cmake_minimum_required(VERSION 2.8.3)
project(ibeo_scala)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
)

catkin_package()


find_package(Boost REQUIRED COMPONENTS system)

include_directories(${catkin_INCLUDE_DIRS}
  /home/kyyurtdas/ibeoSDK/src/
)

add_library(${PROJECT_NAME}
   src/ibeo_scala_node.cc
 )

add_executable(${PROJECT_NAME}_node src/ibeo_scala_node.cc)

add_dependencies(${PROJECT_NAME}_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

link_directories(${catkin_LIB_DIRS}  /home/kyyurtdas/ibeoSDK/libs/)

target_link_libraries(${PROJECT_NAME}_node
   ${catkin_LIBRARIES} /home/kyyurtdas/ibeoSDK/libs/libibeosdk.so
)
