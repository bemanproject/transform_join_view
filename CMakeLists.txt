# SPDX-License-Identifier: Apache-2.0 WITH LLVM-exception

cmake_minimum_required(VERSION 3.25)

project(
    beman.transform_join_view # CMake Project Name, which is also the name of the top-level
    # targets (e.g., library, executable, etc.).
    DESCRIPTION "Beman transform_join_view library"
    LANGUAGES CXX
    VERSION 2.2.1
)

# [CMAKE.SKIP_TESTS]
option(
    BEMAN_TRANSFORM_JOIN_VIEW_BUILD_TESTS
    "Enable building tests and test infrastructure. Default: ${PROJECT_IS_TOP_LEVEL}. Values: { ON, OFF }."
    ${PROJECT_IS_TOP_LEVEL}
)

# [CMAKE.SKIP_EXAMPLES]
option(
    BEMAN_TRANSFORM_JOIN_VIEW_BUILD_EXAMPLES
    "Enable building examples. Default: ${PROJECT_IS_TOP_LEVEL}. Values: { ON, OFF }."
    ${PROJECT_IS_TOP_LEVEL}
)

include(CTest)

# Define header-only library
add_library(beman.transform_join_view INTERFACE)
add_library(beman::transform_join_view ALIAS beman.transform_join_view)

target_sources(
    beman.transform_join_view
    INTERFACE
        FILE_SET HEADERS
            BASE_DIRS "${CMAKE_CURRENT_SOURCE_DIR}/include"
            FILES
                "${CMAKE_CURRENT_SOURCE_DIR}/include/beman/transform_join_view/identity.hpp"
)

target_compile_features(beman.transform_join_view INTERFACE cxx_std_20)

if(BEMAN_TRANSFORM_JOIN_VIEW_BUILD_TESTS)
    add_subdirectory(tests/beman/transform_join_view)
endif()

if(BEMAN_TRANSFORM_JOIN_VIEW_BUILD_EXAMPLES)
    add_subdirectory(examples)
endif()
