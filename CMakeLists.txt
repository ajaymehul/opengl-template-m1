cmake_minimum_required(VERSION 3.24)
project(OpenGLCourseApp)

if (DEFINED ENV{CLION_IDE})
    add_compile_options(-isysroot ${CMAKE_OSX_SYSROOT})
endif()

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_CXX_STANDARD 11)

set(CMAKE_VERBOSE_MAKEFILE 1)
set(APP_VERSION_MAJOR 1)
set(APP_VERSION_MINOR 0)
set(CMAKE_APPLE_SILICON_PROCESSOR 1)

set(APP_TARGET main)

include_directories(${PROJECT_SOURCE_DIR})
add_executable(${APP_TARGET} main.cpp)
target_link_libraries(${APP_TARGET})

# glfw
#find_package(glfw3 REQUIRED)
#include_directories(${GLFW_INCLUDE_DIRS})
#link_libraries(${GLFW_LIBRARY_DIRS})
add_subdirectory(${PROJECT_SOURCE_DIR}/lib/glfw-3.3.8/)

# opengl
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

# glew
find_package(GLEW REQUIRED)
#include_directories(${GLEW_INCLUDE_DIRS})
#set(GLEW_INCLUDE_DIR "${PROJECT_SOURCE_DIR}/lib/glew-2.2.0")



target_link_libraries(
        ${APP_TARGET}
        glfw
        ${OPENGL_LIBRARIES}
        GLEW::GLEW
        ${EXTRA_LIBS}
)

add_executable(OpenGLCourseApp main.cpp)
