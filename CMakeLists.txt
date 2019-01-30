cmake_minimum_required(VERSION 3.9)
project(BLISS)

include(GNUInstallDirs)
add_library(bliss-0.73 STATIC
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
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/bliss-0.73>)

install(DIRECTORY src/bliss-0.73 DESTINATION ${CMAKE_INSTALL_INCLUDEDIR} FILES_MATCHING PATTERN "*.hh")
install(TARGETS bliss-0.73
	EXPORT blissConfig
	RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
	ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
	LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
	INCLUDES DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(EXPORT blissConfig DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/bliss)
