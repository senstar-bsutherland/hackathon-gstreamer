cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_POSITION_INDEPENDENT_CODE ON)

# Specify the version of the library (optional)
set(SENSTAR_GSTREAMER_PLUGINS_VERSION 1.0.0)

project(hackathon-gstreamer LANGUAGES C)

find_package(PkgConfig REQUIRED)
pkg_check_modules(GSTREAMER REQUIRED gstreamer-1.0)
pkg_check_modules(GST_APP REQUIRED gstreamer-app-1.0)

include_directories(
    ${GSTREAMER_INCLUDE_DIRS}
)

set(SOURCES
    basic-tutorial-1.c
)

add_executable(${PROJECT_NAME} basic-tutorial-1.c)

target_link_libraries(${PROJECT_NAME} PUBLIC ${GSTREAMER_LIBRARIES})
target_link_libraries(${PROJECT_NAME} PUBLIC $ENV{GST_PLUGIN_PATH}/libgstsenstardebug.so)

