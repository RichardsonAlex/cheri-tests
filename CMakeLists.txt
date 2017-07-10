cmake_minimum_required(VERSION 3.8)
project(cheri-tests)


include(GNUInstallDirs)

function(add_cheri_test_program _name)
  add_executable(${_name}_dynamic ${ARGN})
  add_executable(${_name}_static ${ARGN})
  target_link_libraries(${_name}_static -static -fuse-ld=bfd)
  install(TARGETS ${_name}_static ${_name}_dynamic RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
endfunction()

add_subdirectory(minimal)
add_subdirectory(minimal_cxx)
