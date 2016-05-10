cmake_minimum_required(VERSION 3.4)
project(helloWorld)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS 1)
include_directories(${CMAKE_BINARY_DIR})
ADD_LIBRARY(MyLibrary SHARED myShared.cpp)
set(SOURCE_FILES main.cpp)


add_executable(mainProgram ${SOURCE_FILES})
TARGET_LINK_LIBRARIES(mainProgram MyLibrary)
INSTALL(TARGETS MyLibrary DESTINATION lib)
INSTALL(TARGETS mainProgram DESTINATION bin)
