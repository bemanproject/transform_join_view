# SPDX-License-Identifier: Apache-2.0 WITH LLVM-exception

include(FetchContent)

FetchContent_Declare(
    Catch2
    GIT_REPOSITORY https://github.com/catchorg/Catch2.git
    GIT_TAG v3.8.0
)
FetchContent_MakeAvailable(Catch2)

add_executable(beman.transform_join_view.tests)
target_sources(beman.transform_join_view.tests PRIVATE transform_view_join.test.cpp)
target_link_libraries(
    beman.transform_join_view.tests
    PRIVATE beman::transform_join_view Catch2::Catch2WithMain
)

include(Catch)
catch_discover_tests(beman.transform_join_view.tests)
