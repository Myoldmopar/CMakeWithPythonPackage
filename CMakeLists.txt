cmake_minimum_required(VERSION 3.16)
project(FakeEPlusWithPythonGuiApp)

set(CMAKE_CXX_STANDARD 17)

# Build C++ application
add_executable(FakeEPlusWithPythonGuiApp cpp_application/main.cpp)

# Packaging of C++ application
# option(BUILD_PACKAGE "Build package" OFF)
set(CPACK_PACKAGE_NAME "CmakeAppWithPythonPackaging")
set(CPACK_PACKAGE_VENDOR "MyComp")
set(CPACK_VERBATIM_VARIABLES true)
set(CPACK_PACKAGE_VERSION_MAJOR 0)
set(CPACK_PACKAGE_VERSION_MINOR 2)
set(CPACK_PACKAGE_VERSION_PATCH 0)
include(CPack)
install(TARGETS FakeEPlusWithPythonGuiApp)

# Packaging of Python GUI application
execute_process(COMMAND "pyinstaller" "--onefile" "${CMAKE_SOURCE_DIR}/python_gui/gui.py")
if (WIN32)
    install(FILES ${CMAKE_BINARY_DIR}/dist/gui.exe DESTINATION "./")
else ()
    install(FILES ${CMAKE_BINARY_DIR}/dist/gui DESTINATION "./")
endif ()