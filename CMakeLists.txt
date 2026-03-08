cmake_minimum_required(VERSION 3.10)
project(imder)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

find_package(Qt5 REQUIRED COMPONENTS Widgets Core Gui)
find_package(OpenCV REQUIRED)

add_executable(imder imder_linux.cpp)

target_link_libraries(imder
    Qt5::Widgets
    Qt5::Core
    Qt5::Gui
    ${OpenCV_LIBS}
    pthread
    GL
)

# Copy icon if present
if(EXISTS "${CMAKE_SOURCE_DIR}/imder.png")
    configure_file(imder.png ${CMAKE_BINARY_DIR}/imder.png COPYONLY)
endif()
