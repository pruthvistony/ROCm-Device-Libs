##===--------------------------------------------------------------------------
##                   ROCm Device Libraries
##
## This file is distributed under the University of Illinois Open Source
## License. See LICENSE.TXT for details.
##===--------------------------------------------------------------------------

cmake_minimum_required(VERSION 2.6)

if(UNIX)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -fno-rtti")
endif()

add_definitions(${LLVM_DEFINITIONS})
include_directories(${LLVM_INCLUDE_DIR})
include_directories(${LLVM_CONFIG_INCLUDE_DIR})
include_directories(${LLVM_MAIN_INCLUDE_DIR})

add_executable(prepare-builtins prepare-builtins.cpp)
llvm_map_components_to_libnames(llvm_libs support core bitreader bitwriter)
target_link_libraries(prepare-builtins ${llvm_libs})
