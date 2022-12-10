cmake_minimum_required(VERSION 3.10)
project(renalog VERSION 1.10)

set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 11)

option(BUILD_RELEASE            "build release edition library" ON)
option(BUILD_SHARED             "build shared library"          ON)
option(BUILD_STATIC             "build static library"          ON)
option(BUILD_LOGREADER_FUNCTION "build renalog reader"          ON)

if(BUILD_RELEASE)

    set(CMAKE_BUILD_TYPE "Release")

else()

    set(CMAKE_BUILD_TYPE "Debug")
    
endif()

include_directories(include)
add_subdirectory(src)

if(NOT BUILD_SHARED AND NOT BUILD_STATIC)

    message(FATAL "must build one shared or static library")

endif()

if(BUILD_SHARED)

    add_library(renalog SHARED
        ${SRC_LIST}
    )
    install(
        TARGETS     renalog
        DESTINATION bin
    )

endif()

if(BUILD_STATIC)

    add_library(renalog_static STATIC
        ${SRC_LIST}
    )
    install(
        TARGETS     renalog_static
        DESTINATION lib
    )

endif()

if(BUILD_LOGREADER_FUNCTION)

    set(HEADERS_LIST
        ${PROJECT_SOURCE_DIR}/include/renalog.h
        ${PROJECT_SOURCE_DIR}/include/renalog_basic.h
        ${PROJECT_SOURCE_DIR}/include/renalog_core.h
        ${PROJECT_SOURCE_DIR}/include/renalog_read.h
    )

else()

    set(HEADERS_LIST
        ${PROJECT_SOURCE_DIR}/include/renalog.h
        ${PROJECT_SOURCE_DIR}/include/renalog_basic.h
        ${PROJECT_SOURCE_DIR}/include/renalog_core.h
    )

endif()

install(FILES
            ${HEADERS_LIST}
        DESTINATION include/renalog
)