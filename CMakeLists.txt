cmake_minimum_required(VERSION 3.0.2)
project(frozen CXX)

option(FROZEN_ENABLE_TESTS   "Enable tests for project"                ON)
option(FROZEN_ENABLE_INSTALL "Add install targets for project headers" ON)

add_library(frozen INTERFACE)
target_include_directories(frozen INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>)

if (FROZEN_ENABLE_TESTS)
    include(CTest)
    enable_testing()

    add_subdirectory(tests)
endif()

if(FROZEN_ENABLE_INSTALL)
    install(TARGETS frozen
            INCLUDES DESTINATION "include")

    # copy headers with h/hpp extensions via regex
    install(DIRECTORY   "include/frozen/"
            DESTINATION "include/frozen"
            FILES_MATCHING
            REGEX ".*\\.h(pp)?")
endif()

