cmake_minimum_required(VERSION 3.0)
project(test_wasm)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/output")
set(CMAKE_EXECUTABLE_SUFFIX ".html")

file(GLOB SOURCES src/*.c)
add_executable(test_wasm ${SOURCES})
set_target_properties(test_wasm PROPERTIES LINK_FLAGS " \
    -s WASM=1 -s EXPORTED_FUNCTIONS='[_plus, _minus]' \
")
