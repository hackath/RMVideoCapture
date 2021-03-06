cmake_minimum_required(VERSION 2.8)

# Define project name
project(masters)

# using C++11 and NEON
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread")

# -mfloat-abi=softfp -mfpu=neon

# Find OpenCV
find_package(OpenCV REQUIRED)

# set(OpenCV_Share_DIRS "/usr/local/lib")

message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")
message(STATUS "    libraries: ${OpenCV_LIBS}")

# Add OpenCV headers location to your include paths
include_directories(${OpenCV_INCLUDE_DIRS})

# link_libraries(${OpenCV_LIBS} ${OpenCV_Share_LIBS})

aux_source_directory(. DIR_SRCS)

# Declare the executable target built from your sources
add_executable(masters ${DIR_SRCS})

# Link your application with OpenCV libraries
target_link_libraries(masters ${OpenCV_LIBS})
