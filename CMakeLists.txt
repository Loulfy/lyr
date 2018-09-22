cmake_minimum_required(VERSION 3.10)
project(lyr)

# ADD GLFW 3
option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
option(GLFW_BUILD_TESTS OFF)
add_subdirectory(libs/glfw)

# ADD VULKAN SDK
message(STATUS "Attempting auto locate Vulkan SDK using CMake...")
find_package(Vulkan)

# C++17
set(CMAKE_CXX_STANDARD 17)

# HEADERS
include_directories(libs/glfw/include libs/plog/include ${Vulkan_INCLUDE_DIR})

# FILES
file(GLOB_RECURSE SOURCES src/*.cpp)
file(GLOB_RECURSE HEADERS src/*.hpp)

# PROJECT
add_library(lyr SHARED ${SOURCES} ${HEADERS})
target_link_libraries(lyr ${Vulkan_LIBRARY} glfw)

# TEST
add_subdirectory(test)