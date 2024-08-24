cmake_minimum_required(VERSION 2.5) 

project(muduo_from_hyacinthus)

set(CMAKE_BUILD_TYPE "Debug")
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#项目会被编译为动态库so， 这是设置动态库的存放路径， 这里是存放到根目录的lib目录下

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

#设置调试信息， and 启动c++11标准
include_directories(${PROJECT_SOURCE_DIR}/include)

link_directories(${PROJECT_SOURCE_DIR}/lib)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=c++11")

add_subdirectory(src)
