cmake_minimum_required(VERSION 3.13)
list(INSERT CMAKE_MODULE_PATH 0 "${CMAKE_CURRENT_LIST_DIR}/cmake/Modules")
include(ABYCacheVariables)
if(ANDROID)
    set(CMAKE_CXX_STANDARD 14)
else()
    set(CMAKE_CXX_STANDARD 17)
endif()
project(ABY LANGUAGES C CXX)
# Write built executables and libraries to bin/ and lib/, respectively.
if(NOT CMAKE_RUNTIME_OUTPUT_DIRECTORY)
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}/bin")
endif()
if(NOT CMAKE_LIBRARY_OUTPUT_DIRECTORY)
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}/lib")
endif()
if(NOT CMAKE_ARCHIVE_OUTPUT_DIRECTORY)
    set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}/lib")
endif()

add_subdirectory(src/abycore)

if(ABY_BUILD_EXE)
    #add_subdirectory(src/test)
    add_subdirectory(src/examples)
endif(ABY_BUILD_EXE)

