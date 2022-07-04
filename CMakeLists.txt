# Copyright 2019 Peter Dimov
# Distributed under the Boost Software License, Version 1.0.
# See accompanying file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt

if(NOT DEFINED IDF_TARGET)

cmake_minimum_required(VERSION 3.5...3.16)

project(boost_endian VERSION "${BOOST_SUPERPROJECT_VERSION}" LANGUAGES CXX)

add_library(boost_endian INTERFACE)
add_library(Boost::endian ALIAS boost_endian)

target_include_directories(boost_endian INTERFACE include)

target_link_libraries(boost_endian
  INTERFACE
    Boost::config
    Boost::core
    Boost::static_assert
    Boost::type_traits
)

if(BUILD_TESTING)

  add_subdirectory(test)

endif()

else()

idf_component_register(
    INCLUDE_DIRS
        include
    REQUIRES
        boost_config
        boost_core
        boost_static_assert
        boost_type_traits
)

endif()

