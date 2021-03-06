cmake_minimum_required(VERSION 3.0.0)
project(GLLearn VERSION 0.1.0)

# 使用 C++ 11 标准
set(CMAKE_CXX_STANDARD 11)

# 添加头文件
set(GLAD_H /usr/local/Cellar/glad/include)
set(GLFW_H /usr/local/include)
set(GLEW_H /usr/local/Cellar/glew/2.2.0_1/include)
include_directories(${GLAD_H} ${GLFW_H} ${GLEW_H}) 

# 添加目标链接
set(GLFW_LINK /usr/local/lib/libglfw.3.dylib)
set(GLEW_LINK /usr/local/Cellar/glew/2.2.0_1/lib/libGLEW.2.2.0.dylib)
link_libraries(${GLFW_LINK} ${GLEW_LINK})

# 执行编译命令
set(SOURCES src/glad.c src/main.cpp)
add_executable(GLLearn ${SOURCES})

# 链接系统的 OpenGL 框架
if (APPLE)
    target_link_libraries(GLLearn "-framework OpenGL")
endif()

include(CTest)
enable_testing()

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)