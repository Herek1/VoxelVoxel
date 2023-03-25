#BASIC
cmake_minimum_required(VERSION 3.18)
project(VoxelVoxel)

set(CMAKE_CXX_STANDARD 23)

#IMPORT
include(FetchContent)
FetchContent_Declare(
        raylib
        GIT_REPOSITORY https://github.com/raysan5/raylib
        GIT_TAG master
        GIT_PROGRESS TRUE
)

FetchContent_MakeAvailable(raylib)


#SOURCE
include_directories(${CMAKE_CURRENT_LIST_DIR}/include)

file(
        GLOB_RECURSE SOURCES
        LIST_DIRECTORIES true
        CONFIGURE_DEPENDS true
        ${CMAKE_CURRENT_LIST_DIR}/src/*.cpp
        ${CMAKE_CURRENT_LIST_DIR}/include/*.h
        ${CMAKE_CURRENT_LIST_DIR}/include/*.hpp
)


#TARGET
add_executable(
        ${CMAKE_PROJECT_NAME}_main
        ${SOURCES}
)
target_link_libraries(
        ${CMAKE_PROJECT_NAME}_main
        raylib
)