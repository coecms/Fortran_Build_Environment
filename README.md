# Basic CMake Setup for a new Fortran Project

The idea is that you can fork this project into your own system, and you immediately have
a structure and a surrounding CMake environment to compile and test.

## Basic usage

After you have cloned this repo, go into its main directory and type the following:

    mkdir bld
    cd bld
    cmake ..
    make -j
    make install

This should build a tiny library `lib/static/liblib1.a` with a single funtion `is_two(n)`
which returns `.T.` if and only if the only parameter is indeed 2, and `.F.` otherwise,
and a single program `bin/exe1` that will write "Hello World" and check for each number in 1..5 whether
this number is indeed 2.

If you have pFUnit installed, it should also manage to write a unit test `test/test1` that tests the library.
