#
# project: sokol-tools
#
cmake_minimum_required(VERSION 3.0)
set(CMAKE_CXX_STANDARD 11)
project(sokol-tools)

# include the fips main cmake file
get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
include("${FIPS_ROOT_DIR}/cmake/fips.cmake")

fips_setup()
if (FIPS_CLANG OR FIPS_GCC)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-missing-field-initializers")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-missing-field-initializers")
endif()
if (FIPS_GCC)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-missing-braces")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-missing-braces")
endif()
fips_ide_group(ext)
fips_add_subdirectory(ext)
fips_ide_group("")
fips_add_subdirectory(src)
fips_finish()


