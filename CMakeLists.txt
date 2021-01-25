cmake_minimum_required(VERSION 2.8)
project(ARTSynchronized)

if( NOT CMAKE_BUILD_TYPE )
    message(STATUS "No build type selected, default to Release")
    set( CMAKE_BUILD_TYPE Release)
else()
    message(STATUS "Build type is set to ${CMAKE_BUILD_TYPE}")
endif()

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra -march=native -g")

find_library(TbbLib tbb)
find_package (Threads)

set(ART_FILES
  OptimisticLockCoupling/Tree.cpp
  ROWEX/Tree.cpp
  ART/Tree.cpp
)

add_library(
  ARTSynchronized

  ${ART_FILES}
)

target_include_directories(
  ARTSynchronized

  PUBLIC
  ${CMAKE_CURRENT_SOURCE_DIR}
)

if(NOT APPLE)
    # Do not use jemalloc on Mac as we cannot properly replace the allocator.
    target_link_libraries(ARTSynchronized PUBLIC jemalloc)
    target_compile_definitions(ARTSynchronized PUBLIC COMPILED_WITH_JEMALLOC)
endif()

target_link_libraries(ARTSynchronized PUBLIC ${TbbLib} ${CMAKE_THREAD_LIBS_INIT})

set(SOURCE_FILES example.cpp)
add_executable(example ${SOURCE_FILES})
target_link_libraries(example ARTSynchronized)