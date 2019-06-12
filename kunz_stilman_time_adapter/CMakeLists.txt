cmake_minimum_required(VERSION 2.8.3)
project(kunz_stilman_time_adapter)
add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  moveit_core
  roscpp
)

# find_package(Boost REQUIRED COMPONENTS system)
catkin_package(
#  INCLUDE_DIRS include
  LIBRARIES kunz_stilman_time_adapter
  CATKIN_DEPENDS moveit_core roscpp
  DEPENDS
)
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

 add_library(${PROJECT_NAME}
   src/${PROJECT_NAME}/kunz_stilman_time_adapter.cpp
 )
 add_dependencies(${PROJECT_NAME} ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
# target_link_libraries(${PROJECT_NAME}
#   ${catkin_LIBRARIES}
# )

 install(TARGETS ${PROJECT_NAME}
   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
   LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
 )

 install(DIRECTORY include/${PROJECT_NAME}/
   DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
   FILES_MATCHING PATTERN "*.h"
   PATTERN ".svn" EXCLUDE
 )

## Mark other files for installation (e.g. launch and bag files, etc.)
# install(FILES
#   # myfile1
#   # myfile2
#   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
# )

