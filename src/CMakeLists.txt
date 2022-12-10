if(BUILD_LOGREADER_FUNCTION)

    set(SRC_LIST
        ${CMAKE_CURRENT_SOURCE_DIR}/renalog_core.cpp
        ${CMAKE_CURRENT_SOURCE_DIR}/renalog_read.cpp
    PARENT_SCOPE)

else()

    set(SRC_LIST
        ${CMAKE_CURRENT_SOURCE_DIR}/renalog_core.cpp
    PARENT_SCOPE)

endif()