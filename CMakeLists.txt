cmake_minimum_required(VERSION 3.10)
project(planning)
set(CMAKE_CXX_STANDARD 11)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/bin) #动态库和exe都指定到bin目录下面
#CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/bin     # 这是在lunix平台下
#CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/bin     #  这是静态库

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)

add_library(common SHARED ${SRC_LISTS})
target_include_directories(common PUBLIC ${PROJECT_SOURCE_DIR}/include)


add_executable(planning_main planning_main.cpp)
target_include_directories(planning_main PUBLIC ${PROJECT_SOURCE_DIR}/include)

target_link_libraries(planning_main PUBLIC common)