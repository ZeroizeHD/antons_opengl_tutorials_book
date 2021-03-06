cmake_minimum_required(VERSION 3.6)   # CMake version check
project(antons_tutorials C CXX)               # Create project "simple_example"
set(CMAKE_CXX_STANDARD 11)            # Enable c++11 standard

#add source folder so the program can be compiled at build folder
include_directories(${CMAKE_SOURCE_DIR})

#Headers
file(GLOB HEADERS
  *.h
  *.cpp
  )

#Main
set(SOURCE_FILES main.c)
add_executable(hotreload ${SOURCE_FILES} ${HEADERS})

#OpenGL
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIR})

target_link_libraries(hotreload ${OPENGL_gl_LIBRARY})


#GLFW
find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)
include_directories(${GLFW_INCLUDE_DIRS})
target_link_libraries(hotreload ${GLFW_LIBRARIES})

#GLEW
find_package(GLEW REQUIRED)
if (GLEW_FOUND)
    include_directories(${GLEW_INCLUDE_DIRS})
    target_link_libraries(hotreload ${GLEW_LIBRARIES})
endif()



