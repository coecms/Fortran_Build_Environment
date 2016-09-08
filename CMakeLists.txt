cmake_minimum_required(VERSION 3.5)

project(build_test)

enable_language(Fortran)

set(CMAKE_Fortran_MODULE_DIRECTORY ${PROJECT_BINARY_DIR}/generated/mods)

include_directories(${CMAKE_Fortran_MODULE_DIRECTORY})
file(MAKE_DIRECTORY ${CMAKE_Fortran_MODULE_DIRECTORY})

set(CMAKE_INSTALL_PREFIX ${PROJECT_BINARY_DIR})

add_subdirectory(libraries)
add_subdirectory(executables)
#add_subdirectory(projects)
