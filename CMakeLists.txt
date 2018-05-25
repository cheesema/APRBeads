cmake_minimum_required(VERSION 3.10)
project(APRBead)

# Additional Benchmarks for APR main paper.

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

##########################################################################
# Configure and use submodules
##########################################################################

find_package(HDF5 REQUIRED)
find_package(TIFF REQUIRED)

include_directories(${HDF5_INCLUDE_DIRS})

# APR
set(APR_TESTS OFF CACHE BOOL "" FORCE)
set(APR_BUILD_STATIC_LIB ON CACHE BOOL "" FORCE)
set(APR_BUILD_SHARED_LIB OFF CACHE BOOL "" FORCE)
set(APR_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(APR_USE_CUDA OFF CACHE BOOL "" FORCE)
add_subdirectory("LibAPR")
set(APR_LIB staticLib)

# Google TEST
set(BUILD_GMOCK OFF CACHE BOOL "" FORCE)
set(BUILD_GTEST ON CACHE BOOL "" FORCE)
set(INSTALL_GTEST OFF CACHE BOOL "" FORCE)

set(GTEST_LIBRARIES gtest)
include_directories(LibAPR/src)

# Benchmark LIB

##########################################################################
# APP stuff
##########################################################################

add_executable(Example_get_apr exec/Example_get_apr.cpp)
target_link_libraries(Example_get_apr ${APR_LIB} ${GTEST_LIBRARIES}  ${HDF5_LIBRARIES} ${TIFF_LIBRARIES})
