cmake_minimum_required(VERSION 3.25)

project(
    parent_1
    VERSION 0.0.1
    DESCRIPTION "A parent project"
    LANGUAGES CXX
)

include(FetchContent)

FetchContent_Declare(
    platform_a
    GIT_REPOSITORY https://github.com/cmake-paul/platform_a.git
    GIT_TAG main
)

FetchContent_Declare(
    util_A
    GIT_REPOSITORY https://github.com/cmake-paul/util_a.git
    GIT_TAG main
)

FetchContent_MakeAvailable(platform_a util_A)

add_executable(main)

add_subdirectory(include)
add_subdirectory(src)

target_link_libraries(
    main
    PRIVATE
    util_A
)
