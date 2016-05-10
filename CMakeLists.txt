cmake_minimum_required(VERSION 3.4)
project(helloWorld)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
include(GenerateExportHeader)
include_directories(${CMAKE_BINARY_DIR})
ADD_LIBRARY(MyLibrary myShared.cpp)
set(SOURCE_FILES main.cpp)

GENERATE_EXPORT_HEADER( MyLibrary
             BASE_NAME MyLibrary
             EXPORT_MACRO_NAME SHARED_EXPORT
             EXPORT_FILE_NAME shared_EXPORT.h
             STATIC_DEFINE MyLibrary_BUILT_AS_STATIC
        )
INSTALL(TARGETS MyLibrary DESTINATION bin)
INSTALL(FILES myShared.h DESTINATION include)

add_executable(mainProgram ${SOURCE_FILES})
TARGET_LINK_LIBRARIES(mainProgram MyLibrary)
#TARGET_INCLUDE_DIRECTORIES(mainProgram PUBLIC ${CMAKE_BINARY_DIR}/exports)
