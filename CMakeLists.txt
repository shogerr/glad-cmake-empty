cmake_minimum_required(VERSION 3.15)
project(glad)

add_library(glad src/glad.c)
target_include_directories(glad PUBLIC include)

# Release build is slow with MSVC, so don't optimize.
if(MSVC)
	target_compile_options(glad PRIVATE /Od)
endif()

install(TARGETS glad EXPORT gladTargets)
