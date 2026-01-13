cmake_minimum_required(VERSION 3.0...3.29)

project(wdd VERSION 0.2.1)

add_executable(wdd src/wdd.c)

install(TARGETS wdd RUNTIME DESTINATION .)

if(NOT CMAKE_GENERATOR_PLATFORM)
  set(CMAKE_GENERATOR_PLATFORM "x64")  # Или дефолт
endif()

string(TOLOWER ${CMAKE_GENERATOR_PLATFORM} _arch)

set(CPACK_GENERATOR ZIP)
set(CPACK_PACKAGE_FILE_NAME
    ${PROJECT_NAME}-${PROJECT_VERSION}-${_arch})

include(CPack)
