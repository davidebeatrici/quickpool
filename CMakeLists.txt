cmake_minimum_required(VERSION 3.0.0)
project(quickpool VERSION 1.2.0)

## Project-wide setup
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED YES)
set(CMAKE_CXX_EXTENSIONS NO)

find_package(Threads)

add_executable(test test.cpp)
target_link_libraries(test ${CMAKE_THREAD_LIBS_INIT})
if(CMAKE_SYSTEM_NAME STREQUAL "Linux")
  target_link_libraries(test "-latomic")
endif()

# set (CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -fno-omit-frame-pointer -fsanitize=address,undefined,leak,bounds,alignment")
# set (CMAKE_LINKER_FLAGS_DEBUG "${CMAKE_LINKER_FLAGS_DEBUG} -fno-omit-frame-pointer -fsanitize=address,undefined,leak,bounds,alignment")


set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
