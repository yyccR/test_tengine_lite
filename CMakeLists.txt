cmake_minimum_required(VERSION 3.17)
project(test_tengine)

set(CMAKE_CXX_STANDARD 17)

find_package(OpenCV REQUIRED core imgproc highgui)
include_directories(${OpenCV_INCLUDE_DIRS})

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/tengine-lite-1.5/include)

add_library(tengine_lite SHARED IMPORTED)
set_target_properties(tengine_lite PROPERTIES IMPORTED_LOCATION
        ${CMAKE_CURRENT_LIST_DIR}/tengine-lite-1.5/libtengine-lite.dylib)


add_executable(test_tengine ./ultralytics:yolov3/ultralytics_yolov3.cpp)
target_link_libraries(test_tengine tengine_lite)