cmake_minimum_required(VERSION 3.1)
project(Triangulation)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

# OpenMesh
find_package(OpenMesh REQUIRED)
include_directories(${OPENMESH_INCLUDE_DIRS})

# Qt5
set(CMAKE_SHARED_LIBRARY_LINK_CXX_FLAGS "")
set(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "")

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

if(CMAKE_VERSION VERSION_LESS "3.7.0")
	set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()

add_definitions(-O2 -D_FILE_OFFSET_BITS=64 -fPIC)

find_package(PkgConfig)
find_package(Qt5Widgets)
find_package(Qt5OpenGL)
find_package(Qt5Gui)
find_package(OpenGL)
set(plugins Qt5::OpenGL Qt5::Gui)

# Add your project files
file(GLOB SRCFILES src/*.cc)
file(GLOB HDRFILES src/*.hh)
add_executable(triangulation src/main.cpp ${SRCFILES} ${HDRFILES})

qt5_use_modules(triangulation Core Gui Widgets OpenGL)

target_link_libraries(triangulation
    OpenMeshCore
    OpenMeshTools
    Qt5::OpenGL
    ${QT_LIBRARIES}
    ${OPENGL_LIBRARIES})
