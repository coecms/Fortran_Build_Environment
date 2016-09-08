cmake_minimum_required(VERSION 3.5)

project(build_test)

enable_language(Fortran)

set(CMAKE_Fortran_MODULE_DIRECTORY ${PROJECT_BINARY_DIR}/generated/mods)

include_directories(${CMAKE_Fortran_MODULE_DIRECTORY})
file(MAKE_DIRECTORY ${CMAKE_Fortran_MODULE_DIRECTORY})

set(CMAKE_INSTALL_PREFIX ${PROJECT_BINARY_DIR})

add_subdirectory(libraries)
add_subdirectory(executables)

set(PFUNIT_DIR $ENV{PFUNIT})
IF(IS_DIRECTORY ${PFUNIT_DIR})
    message(STATUS "pFUnit found in ${PFUNIT_DIR}")
    add_subdirectory(tests)

    # Add compiler flags for testing
    if(CMAKE_Fortran_COMPILER_ID MATCHES GNU)
        message(STATUS "adding compiler flags for code coverage")
        set(CMAKE_Fortran_FLAGS "${CMAKE_Fortran_FLAGS} -g -fprofile-arcs -ftest-coverage")
    endif()

    enable_testing()
    # Add the tests below
    add_test(NAME Test COMMAND test1)
ELSE()
    message(WARNING "pFUnit not installed, testing disabled")
ENDIF()
