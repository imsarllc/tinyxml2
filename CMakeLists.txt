cmake_minimum_required (VERSION 3.21)

if (TARGET tinyxml2)
  get_target_property(tinyxml2_loc tinyxml2 SOURCE_DIR)
  message("NOT including tinyxml2 from ${CMAKE_CURRENT_LIST_DIR}")
  message("Tinyxml2 was included from ${tinyxml2_loc}")
  return()
else()
  set(TIXML_USE_STL TRUE)
endif()

add_library(tinyxml2 OBJECT)
add_library(tinyxml2::tinyxml2 ALIAS tinyxml2)

set_target_properties(tinyxml2
  PROPERTIES POSITION_INDEPENDENT_CODE ON
)

target_sources(tinyxml2 PRIVATE
  src/tinyxml2.cpp
)

target_include_directories(tinyxml2
  PUBLIC include
  PRIVATE include/tinyxml2
  )
