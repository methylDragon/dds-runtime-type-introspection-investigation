# (c) 2018 Copyright, Real-Time Innovations, Inc. All rights reserved.
# No duplications, whole or partial, manual or electronic, may be made
# without express written permission.  Any such copies, or revisions thereof,
# must display this notice unaltered.
# This code contains trade secrets of Real-Time Innovations, Inc.
cmake_minimum_required(VERSION 3.11)
project(cpp-rtiexamples-dynamic-data-using-publisher-subscriber)
set(CMAKE_MODULE_PATH
    ${CMAKE_MODULE_PATH}
    "${CMAKE_CURRENT_SOURCE_DIR}/../../../resources"
)

# Include ConnextDdsAddExample.cmake from resources/cmake
include(ConnextDdsAddExample)

connextdds_add_example(
    IDL "Shapes"
    LANG "C++11"
    NO_REQUIRE_QOS
)

install(FILES
  ${CMAKE_CURRENT_BINARY_DIR}/Shapes_publisher
  ${CMAKE_CURRENT_BINARY_DIR}/Shapes_subscriber
  DESTINATION bin/${PROJECT_NAME})
