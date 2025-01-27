cmake_minimum_required(VERSION 3.14)
project(qwt LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

find_package(Qt6 COMPONENTS
        Core
        Widgets
        OpenGLWidgets
        Svg
        PrintSupport
        Concurrent
        REQUIRED)

include_directories(src/)

file(
        GLOB_RECURSE HEADERS
        "src/*.h"
)

file(
        GLOB_RECURSE SOURCES
        "src/*.cpp"
)

list(REMOVE_ITEM HEADERS "${CMAKE_CURRENT_SOURCE_DIR}/src/qwt_plot_glcanvas.h")
list(REMOVE_ITEM SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/src/qwt_plot_glcanvas.cpp")

add_library(${PROJECT_NAME} ${SOURCES} ${HEADERS})
target_link_libraries(${PROJECT_NAME}
        Qt::Core
        Qt::Widgets
        Qt::OpenGLWidgets
        Qt::Svg
        Qt::PrintSupport
        Qt::Concurrent
)