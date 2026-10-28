cmake_minimum_required(VERSION 3.39 FATAL_ERROR)

project(
    C++Calc
    VERSION 1.0.0
    LANGUAGES CXX
)

include(FetchContent)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(wxBUILD_SHARED OFF)

FetchContent_declare(
    wxWidgets
    GIT_REPOSITORY https://github.com/wxWidgets/wxWidgets.git
    GIT_TAG v3.2.11
    GIT_SHALLOW ON
)

FetchContent_MakeAvailable(wxWidgets)

set(SRCS main.cpp)

add_executable(main WIN32 ${SRCS})

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT main)

target_link_libraries(main PRIVATE wxcore wxnet)