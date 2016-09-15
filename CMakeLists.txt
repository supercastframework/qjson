cmake_minimum_required(VERSION 2.8)

project(qjson)

set(JSON_SRC
    qjson.h
    qjson.cpp)

# qt
set (JSON_QT_LIBRARIES "")
set (JSON_QT_INCLUDES "")

find_package(Qt4 QUIET)

if (QT4_FOUND)

    find_package (Qt4 REQUIRED QtCore)
    include (${QT_USE_FILE})
    set (JSON_QT_INCLUDES
        ${Qt4Core_INCLUDE_DIRS})

    set (JSON_QT_LIBRARIES ${QT_LIBRARIES})

else()

    find_package(Qt5Core REQUIRED)
    set (JSON_QT_INCLUDES
        ${Qt5Core_INCLUDE_DIRS})
    set (JSON_QT_LIBRARIES
        Qt5::Core)

endif(QT4_FOUND)

include_directories (
    .
    ${JSON_QT_INCLUDES})
add_library(qjson ${JSON_SRC})
target_link_libraries(qjson ${JSON_QT_LIBRARIES})
