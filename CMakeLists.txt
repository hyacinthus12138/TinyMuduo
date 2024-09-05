cmake_minimum_required(VERSION 2.5) 

project(TinyMuduo)

set(CMAKE_BUILD_TYPE "Debug")
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#项目会被编译为动态库so， 这是设置动态库的存放路径， 这里是存放到根目录的lib目录下

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

#设置调试信息， and 启动c++11标准
include_directories(${PROJECT_SOURCE_DIR}/include)

link_directories(${PROJECT_SOURCE_DIR}/lib)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=c++11")

# 列出所有需要编译的源文件
file(GLOB SRC_LIST
    src/*.cpp
)
add_library(TinyMuduo SHARED ${SRC_LIST})

# 测试代码
add_subdirectory(test)



# -------------------------------------- install --------------------------------------
# 设置安装前缀
set(CMAKE_INSTALL_PREFIX /usr/local)

# 递归查找所有头文件并安装到同一个目录中
file(GLOB_RECURSE HEADER_FILES
    "${PROJECT_SOURCE_DIR}/include/*.h"
    "${PROJECT_SOURCE_DIR}/include/*.hpp"
)

# 添加头文件安装规则
install(FILES ${HEADER_FILES}
    DESTINATION include/TinyMuduo
)

# 添加库文件安装规则
install(TARGETS TinyMuduo
    LIBRARY DESTINATION lib
)
