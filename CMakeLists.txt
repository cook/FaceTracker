cmake_minimum_required (VERSION 2.8)
project (stasm)

set(CMAKE_INSTALL_PREFIX ${PROJECT_BINARY_DIR}/../bin/ CACHE STRING "" FORCE)
#set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin/ CACHE STRING "" FORCE)
#set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin/ CACHE STRING "" FORCE)

find_package (OpenCV REQUIRED)
include_directories(include ${OpenCV_INCLUDE_DIRS})

file(GLOB lib_src src/lib/*.cc)
add_library(facetracker STATIC ${lib_src})

add_executable(test_facetracker src/exe/face_tracker.cc)
target_link_libraries(test_facetracker facetracker ${OpenCV_LIBS})
