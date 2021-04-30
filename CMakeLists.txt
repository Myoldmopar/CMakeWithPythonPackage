cmake_minimum_required(VERSION 3.19)
project(CmakePythonPackaging)

set(CMAKE_CXX_STANDARD 17)

add_executable(CmakePythonPackaging main.cpp)

# option(BUILD_PACKAGE "Build package" OFF)
set(CPACK_PACKAGE_NAME "CmakePythonPackaging")
set(CPACK_PACKAGE_VENDOR "MyComp")
set(CPACK_VERBATIM_VARIABLES true)
set(CPACK_PACKAGE_VERSION_MAJOR 0)
set(CPACK_PACKAGE_VERSION_MINOR 2)
set(CPACK_PACKAGE_VERSION_PATCH 0)
include(CPack)

install(TARGETS CmakePythonPackaging)
