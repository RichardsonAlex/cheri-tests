cmake_minimum_required(VERSION 3.8)
project(cheri-tests)


function(add_cheri_test_program _name)
  add_executable(${_name}_dynamic ${ARGN})
  add_executable(${_name}_static ${ARGN})
  target_link_libraries(${_name}_static -static)
endfunction()

add_subdirectory(minimal)
add_subdirectory(minimal_cxx)
