cmake_minimum_required(VERSION 3.10)
project(lyr_test)

file(GLOB SOURCE_FILES *.cpp *.hpp)

add_executable(lyr_test ${SOURCE_FILES})
target_link_libraries(lyr_test lyr)