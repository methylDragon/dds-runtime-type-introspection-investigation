# (c) 2019 Copyright, Real-Time Innovations, Inc. All rights reserved.
# No duplications, whole or partial, manual or electronic, may be made
# without express written permission.  Any such copies, or revisions thereof,
# must display this notice unaltered.
# This code contains trade secrets of Real-Time Innovations, Inc.
cmake_minimum_required(VERSION 3.11)
project(cpp-rtiexamples-connext-dds)
set(CMAKE_MODULE_PATH
    ${CMAKE_MODULE_PATH}
    "${CMAKE_CURRENT_SOURCE_DIR}/resources/cmake"
)

include(ConnextDdsAddExamplesSubdirectories)

# Find the ConnextDDS libraries. This will look for core and API libraries
find_package(RTIConnextDDS
    "6.1.1"
    REQUIRED
    COMPONENTS
        core
)

if(STATIC_ANALYSIS)
    find_program(CPPCHECK_EXE NAMES "cppcheck")

    if(CPPCHECK_EXE)
        set(CPPCHECK_CMD
            ${CPPCHECK_EXE}
                --enable=style,unusedFunction
                --suppress=*:*/ndds/*
                --suppress=*:*/src/*
                --quiet
                --relative-paths)
        set(CMAKE_C_CPPCHECK "${CPPCHECK_CMD}")
        set(CMAKE_CXX_CPPCHECK "${CPPCHECK_CMD}")
    endif()

    set(static_analysis_script
        "${CMAKE_CURRENT_SOURCE_DIR}/../../resources/static_analysis/run_static_analysis.py")
    add_custom_target(static_analysis
        COMMAND
            ${static_analysis_script}
                --binary-dir
                ${CMAKE_CURRENT_BINARY_DIR}
                --includes
                ${CONNEXTDDS_INCLUDE_DIRS}
                --defines
                ${CONNEXTDDS_COMPILE_DEFINITIONS}
        COMMENT
            "Running static analysis...")
    set_target_properties(static_analysis
        PROPERTIES
            EXCLUDE_FROM_ALL TRUE)
endif()

set(example_subdirs
  "cpp/dynamic_data_using_publisher_subscriber"
  "cpp/dynamic_data_access_union_discriminator"
  "cpp/dynamic_data_nested_structs"
  "cpp/dynamic_data_request_reply"
  "cpp/dynamic_data_sequences"
)

connextdds_add_examples_subdirectories(
    EXAMPLES
    ${example_subdirs}
)

foreach(subdir ${example_subdirs})
  add_subdirectory(${subdir}/src)
endforeach()
