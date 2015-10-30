
cmake_minimum_required (VERSION 3.0)

project (mari0)

set (IMPORT_DIR ${CMAKE_INSTALL_PREFIX}
     CACHE FILEPATH "Whete to look for exported target scripts")

# Include exported cmake spec from liboda
# The target is named "oda"
include (${IMPORT_DIR}/cmake/liboda.cmake)

configure_file (
  ${CMAKE_SOURCE_DIR}/game/defs.in.lua
  ${CMAKE_SOURCE_DIR}/game/defs.lua
)

configure_file (
  ${CMAKE_SOURCE_DIR}/mari0.in.sh
  ${CMAKE_SOURCE_DIR}/mari0.sh
)

add_custom_target (
  mari0 ALL
  COMMAND cmake -E copy mari0.sh ${CMAKE_BINARY_DIR}
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
)

