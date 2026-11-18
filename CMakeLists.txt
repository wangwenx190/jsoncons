cmake_minimum_required(VERSION 3.25)
project(jsoncons LANGUAGES CXX)
include(GNUInstallDirs)
add_library(jsoncons INTERFACE)
add_library(jsoncons::jsoncons ALIAS jsoncons)
target_compile_features(jsoncons INTERFACE cxx_std_17)
target_include_directories(jsoncons INTERFACE
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>"
    "$<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>")
install(TARGETS jsoncons EXPORT jsonconsTargets)
install(DIRECTORY include/ DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}")
install(EXPORT jsonconsTargets NAMESPACE jsoncons:: FILE jsoncons-config.cmake
    DESTINATION "${CMAKE_INSTALL_LIBDIR}/cmake/jsoncons")
install(FILES LICENSE DESTINATION "${CMAKE_INSTALL_DATADIR}/licenses/jsoncons")
