cmake_minimum_required(VERSION 3.15)
project(duplo)

set(DUPLO_VERSION "\"v1.0.0\"" CACHE STRING "Duplo version")

enable_testing()
add_subdirectory(src)
add_subdirectory(tests)
