cmake_minimum_required(VERSION 3.13)
project(CppAlgorithms)

set(CMAKE_CXX_STANDARD 17)

# bring headers into the project
include_directories(include)

# can manually add individual sources using the set command
# set(SOURCES src/main.cpp)

# however, the file(GLOB...) allows for wildcard additions
# GLOB (or GLOB_RECURSE) creates a list of all files that meet the globbing expression ("src/*.cpp") and adds them to
# the variable SOURCES
file(GLOB SOURCES "src/*.cpp")

# use the ${SOURCES} variable created by file(GLOB...) command rather than an explicit reference to each source file to
# build the final executable
add_executable(CppAlgorithms ${SOURCES})