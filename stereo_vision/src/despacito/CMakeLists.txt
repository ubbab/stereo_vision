cmake_minimum_required(VERSION 2.8.3)

project(despacito)



find_package(catkin REQUIRED COMPONENTS

  cv_bridge

  image_transport

  roscpp
  rospy
  std_msgs

  dynamic_reconfigure

)
find_package(OpenCV)



generate_dynamic_reconfigure_options(

  cfg/dynamic.cfg

)



catkin_package(



  LIBRARIES despacito

  CATKIN_DEPENDS cv_bridge image_transport roscpp dynamic_reconfigure rospy std_msgs



)


include_directories(

${OpenCV_INCLUDE_DIRS}  

${catkin_INCLUDE_DIRS}

)



add_executable(publisher src/publisher.cpp)

add_dependencies(publisher 

    ${catkin_EXPORTED_TARGETS} 

    ${${PROJECT_NAME}_EXPORTED_TARGETS}

)

add_executable(publisher1 src/publisher1.cpp)

add_dependencies(publisher1 

    ${catkin_EXPORTED_TARGETS} 

    ${${PROJECT_NAME}_EXPORTED_TARGETS}

)

add_executable(subscriber src/subscriber.cpp)

add_dependencies(subscriber 

    ${catkin_EXPORTED_TARGETS} 

    ${${PROJECT_NAME}_EXPORTED_TARGETS}

)

 target_link_libraries(publisher

${OpenCV_LIBRARIES}   

${catkin_LIBRARIES}

 )

target_link_libraries(publisher1

${OpenCV_LIBRARIES}   

${catkin_LIBRARIES}

 )


target_link_libraries(subscriber

${OpenCV_LIBRARIES}   

${catkin_LIBRARIES}

 )





