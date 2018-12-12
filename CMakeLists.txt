cmake_minimum_required(VERSION 3.13)

# create a variable to represent the project name
set(PROJECT_NAME "CppAlgorithms")

project(PROJECT_NAME)

set(CMAKE_CXX_STANDARD 17)

# set the build type to be a release build
set(CMAKE_BUILD_TYPE Release)

# bring headers into the project
include_directories(include)

# can manually add individual sources using the set command
# set(SOURCES src/main.cpp)

# however, the file(GLOB...) allows for wildcard additions
# GLOB (or GLOB_RECURSE) creates a list of all files that meet the globbing expression ("src/*.cpp") and adds them to
# the variable SOURCES
file(GLOB SOURCES "src/*.cpp")

# add the folder where google test source files are saved
add_subdirectory(test/lib/googletest-1.8.1)

# use the ${SOURCES} variable created by file(GLOB...) command rather than an explicit reference to each source file to
# build the final executable
add_executable(PROJECT_NAME ${SOURCES})

# generate a library (libCppAlgorithms.so) from the sources
# the library is built as a shared library using the SHARED flag. Other options are STATIC and MODULE
# note: use the `ldd` command to display the shared library dependencies
# add_library(CppAlgorithms SHARED ${SOURCES})

# generates a static library (libCppAlgorithms.a)
# use any archive command (e.g. `ar -t`) to list the contents of the static library
#add_library(PROJECT_NAME STATIC ${SOURCES})

# set the location where the library would be installed
# use `sudo make install` to install the library
# install(TARGETS CppAlgorithms DESTINATION /usr/lib)

# note: use the GNU `nm` command to list the symbols in the object files and binaries.
# the chars T, U and R listed in the output of `nm` map to 'Code', 'Undefined' and 'Read-only data' respectively.

# link your library with google test library
target_link_libraries(PROJECT_NAME gtest gtest_main)

#link your library with google mock library
target_link_libraries(PROJECT_NAME gmock gmock_main)
