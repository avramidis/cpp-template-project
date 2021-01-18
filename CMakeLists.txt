#---------------------------------------------------------------------------//
# Copyright (c) 2021 Eleftherios Avramidis <el.avramidis@gmail.com>
#
# Distributed under The MIT License (MIT)
# See accompanying file LICENSE
#---------------------------------------------------------------------------//

cmake_minimum_required(VERSION 3.16)
project(mysort
        VERSION 1.0.0
        DESCRIPTION "Sort algorithms example implementations.")

# Project dependencies
include(cmake/ProjectDependencies.cmake)

# Cmake project settings
include(cmake/StandardProjectSettings.cmake)

# Standard compiler warnings
include(cmake/CompilerWarnings.cmake)
add_library(${CMAKE_PROJECT_NAME}_project_warnings INTERFACE)
set_project_warnings(${CMAKE_PROJECT_NAME}_project_warnings)

# Project settings
include(cmake/StandardProjectSettings.cmake)
add_library(${CMAKE_PROJECT_NAME}_project_options INTERFACE)
target_compile_features(${CMAKE_PROJECT_NAME}_project_options INTERFACE cxx_std_20)

add_subdirectory(src)
add_subdirectory(examples)
add_subdirectory(tests)
add_subdirectory(benchmarks)

## Executables
#add_executable(buble_sort examples/main.cpp src/utils/Utils.h src/bubble_sort/bubble_sort.h)
#target_link_libraries(buble_sort PUBLIC ${CMAKE_PROJECT_NAME}_project_options ${CMAKE_PROJECT_NAME}_project_warnings)
#
#add_executable(buble_sort_bench src/bubble_sort/benchmark.cpp src/utils/Utils.h src/bubble_sort/bubble_sort.h)
#target_link_libraries(buble_sort_bench PUBLIC benchmark::benchmark benchmark::benchmark_main ${CMAKE_PROJECT_NAME}_project_options ${CMAKE_PROJECT_NAME}_project_warnings)
#target_include_directories(buble_sort_bench PUBLIC ${googlebenchmark_INCLUDE_DIRS})