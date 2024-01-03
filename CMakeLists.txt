cmake_minimum_required(VERSION 3.27)

set(CMAKE_CXX_STANDARD 20)


# --- Fetch FTXUI --------------------------------------------------------------
include(FetchContent)

set(FETCHCONTENT_UPDATES_DISCONNECTED TRUE)
FetchContent_Declare(ftxui
        GIT_REPOSITORY https://github.com/ArthurSonzogni/ftxui
        GIT_TAG v5.0.0
        # Important: Specify a GIT_TAG XXXXX here.
)

FetchContent_GetProperties(ftxui)
if(NOT ftxui_POPULATED)
    FetchContent_Populate(ftxui)
    add_subdirectory(${ftxui_SOURCE_DIR} ${ftxui_BINARY_DIR} EXCLUDE_FROM_ALL)
endif()

# ------------------------------------------------------------------------------

project(tetris
        LANGUAGES CXX
        VERSION 1.0.0
)

add_executable(tetris src/main.cpp)
target_include_directories(tetris PRIVATE src)

target_link_libraries(tetris
        PRIVATE ftxui::screen
        PRIVATE ftxui::dom
        PRIVATE ftxui::component # Not needed for this example.
)

#find_package(Curses REQUIRED)
#include_directories(${CURSES_INCLUDE_DIR})
#
#add_executable(tetris main.cpp
#        shapes.h)
#target_link_libraries(tetris ${CURSES_LIBRARIES})


