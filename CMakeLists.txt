cmake_minimum_required(VERSION 2.8)
cmake_policy(VERSION 2.8)

project( ITK_SPLIT_COMPONENTS )

find_package( ITK REQUIRED )
include( IJMacros.txt )
set( REQUIRED_PACKAGES
  ITK3.20
  )
foreach( package ${REQUIRED_PACKAGES} )
  LOADPACKAGE( ${package} )
endforeach()
include( ${ITK_USE_FILE} )

# where all the executables go
set( CMAKE_RUNTIME_OUTPUT_DIRECTORY
  ${ITK_SPLIT_COMPONENTS_BINARY_DIR}/bin )

include_directories( ${CMAKE_CURRENT_SOURCE_DIR}/Code )
add_subdirectory( Code )

include(CTest)
if(BUILD_TESTING)
  enable_testing()
  add_subdirectory( Testing )
endif(BUILD_TESTING)

