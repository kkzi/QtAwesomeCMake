project(QtAwesome)
cmake_minimum_required(VERSION 3.10)

find_package(Qt5 COMPONENTS core gui widgets)
include_directories(${Qt5Core_INCLUDE_DIRS} ${Qt5Gui_INCLUDE_DIRS} ${Qt5Widgets_INCLUDE_DIRS})

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(QA_ROOT QtAwesome/QtAwesome)
list(APPEND QA_SRCS 
    ${QA_ROOT}/QtAwesome.h ${QA_ROOT}/QtAwesome.cpp 
    ${QA_ROOT}/QtAwesomeAnim.h ${QA_ROOT}/QtAwesomeAnim.cpp
    ${QA_ROOT}/QtAwesome.qrc
)
add_library(FontAwesome STATIC ${QA_SRCS})

include_directories(${QA_ROOT})
add_executable(FontAwesomeSample QtAwesome/QtAwesomeSample/main.cpp)
target_link_libraries(FontAwesomeSample PRIVATE FontAwesome Qt5::Widgets)
