cmake_minimum_required(VERSION 3.15)
project(sibling)

set(CMAKE_CXX_STANDARD 17)

add_executable(sibling main.cpp)
target_include_directories(sibling PUBLIC .)
