cmake_minimum_required(VERSION 3.4)
project(helloWorld)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
ADD_LIBRARY(hello SHARED hello.cpp hello.h)
set(SOURCE_FILES main.cpp)
add_executable(helloWorld ${SOURCE_FILES})
TARGET_LINK_LIBRARIES(helloWorld hello)