cmake_minimum_required(VERSION 3.16)

project(Cpu833SysComReceiver VERSION 0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 6.4 REQUIRED COMPONENTS Quick)

qt_standard_project_setup()

qt_add_executable(appCpu833SysComReceiver
    main.cpp
)

qt_add_qml_module(appCpu833SysComReceiver
    URI Cpu833SysComReceiver
    VERSION 1.0
    QML_FILES Main.qml
)

set_target_properties(appCpu833SysComReceiver PROPERTIES
    MACOSX_BUNDLE_GUI_IDENTIFIER my.example.com
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(appCpu833SysComReceiver
    PRIVATE Qt6::Quick
    PRIVATE ${CMAKE_SOURCE_DIR}/Cpu833SysComReceiver/SysComServer.lib
)

install(TARGETS appCpu833SysComReceiver
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
