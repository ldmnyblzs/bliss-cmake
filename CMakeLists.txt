cmake_minimum_required(VERSION 3.9)
project(BLISS)

option(BUILD_SHARED_LIBS "Build bliss-0.73 as a shared library" ON)

add_library(bliss-0.73
  src/bliss-0.73/defs.cc
  src/bliss-0.73/graph.cc
  src/bliss-0.73/partition.cc
  src/bliss-0.73/orbit.cc
  src/bliss-0.73/uintseqhash.cc
  src/bliss-0.73/heap.cc
  src/bliss-0.73/utils.cc
  src/bliss-0.73/bliss_C.cc)
target_include_directories(bliss-0.73 PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>
  $<INSTALL_INTERFACE:include/bliss-0.73>)

install(DIRECTORY src/bliss-0.73 DESTINATION include FILES_MATCHING PATTERN "*.hh")
install(TARGETS bliss-0.73 EXPORT bliss_target DESTINATION bin)
install(EXPORT bliss_target DESTINATION lib/cmake/bliss-0.73)
