cmake_minimum_required(VERSION 3.0.0)

set(CMAKE_TOOLCHAIN_FILE ${CMAKE_CURRENT_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake
  CACHE STRING "Vcpkg toolchain file")

set(VCPKG_VERBOSE ON)

project(testapp VERSION 0.1.0)

find_package(unofficial-sqlite3 CONFIG REQUIRED)

include(CTest)

enable_testing()

add_executable(testapp main.cpp)
target_link_libraries(testapp PRIVATE unofficial::sqlite3::sqlite3)


set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
 