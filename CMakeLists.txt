cmake_minimum_required(VERSION 3.1.0 FATAL_ERROR)

cmake_policy(SET CMP0048 NEW)
if("${CMAKE_VERSION}" VERSION_LESS "3.13")
    #message(WARNING "CMake ${CMAKE_VERSION} has no CMP0077 policy: options will erase uncached/untyped normal vars!")
else()
    cmake_policy(SET CMP0077 NEW)
endif()

project(sshproxy
    VERSION 0.1.0
    LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

if("${CMAKE_VERSION}" VERSION_LESS "3.7")
    set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()

find_package(Qt5 COMPONENTS Widgets REQUIRED)

add_executable(sshproxy
    MainDialog.cpp
    Indicator.cpp
    main.cpp
    sshproxy.qrc
)

target_link_libraries(sshproxy Qt5::Widgets)

include(GNUInstallDirs)
install(TARGETS sshproxy
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

