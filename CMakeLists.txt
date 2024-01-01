cmake_minimum_required(VERSION 3.27)
project(tetris)

set(CMAKE_CXX_STANDARD 20)

find_package(Curses REQUIRED)
include_directories(${CURSES_INCLUDE_DIR})

add_executable(tetris main.cpp)
target_link_libraries(tetris ${CURSES_LIBRARIES})

