cmake_minimum_required(VERSION 3.10)
project(sylar)

# 设置输出目录
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

# 设置编译选项
set(CMAKE_VERBOSE_MAKEFILE ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0 -g -std=c++11 -Wall -Wno-deprecated -Werror -Wno-unused-function")

# 添加包含目录
include_directories(${PROJECT_SOURCE_DIR})

# 设置库源文件
set(LIB_SRC
    log.cc
    util.cc
)

# 构建共享库
add_library(sylar SHARED ${LIB_SRC})

# 添加测试可执行程序
add_executable(test test/test.cc)
add_dependencies(test sylar)
target_link_libraries(test sylar)
