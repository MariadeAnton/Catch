# CMakeLists.txt
#
# The top-level configuration file for the build system "CMake" of the project
# "Catch".
#
# Author: Phil Nash <github@philnash.me>
#
# Copyright Phil Nash 2013-2015 (http://levelofindirection.com).
#
# Distributed under the Boost Software License, Version 1.0. (See accompanying
# file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt)

if(BIICODE)
  # Biicode build.
  INIT_BIICODE_BLOCK()

  if(APPLE)
    #set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} -x objective-c")
    find_path(COCOA_INCLUDE_DIR Cocoa/Cocoa.h)
    find_path(FOUNDATION_INCLUDE_DIR Foundation/Foundation.h)
  endif()

  ADD_BIICODE_TARGETS()

  set_target_properties(florianwolters_catch_include_internal_catch_default_main
                        florianwolters_catch_single_include_catch
                        PROPERTIES EXCLUDE_FROM_ALL 1
                        LINKER_LANGUAGE C)
else(BIICODE)
  # Independent build.
  cmake_minimum_required(VERSION 2.8)
endif(BIICODE)

add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/projects/CMake")
