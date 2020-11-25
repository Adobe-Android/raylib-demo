cmake_minimum_required(VERSION 3.9...3.19)
project(raylib-demo VERSION 0.1.0 LANGUAGES CXX)

# raylib doesn't have find_package configured
# find_package(raylib REQUIRED)
add_executable(raylib-demo src/main.cpp)
target_compile_features(raylib-demo PUBLIC cxx_std_17)
set_target_properties(raylib-demo PROPERTIES CXX_EXTENSIONS OFF)

target_include_directories(raylib-demo PRIVATE C:/Users/tngam/source/repos/cpp/vcpkg/installed/x86-windows/include)
target_link_directories(raylib-demo PRIVATE C:/Users/tngam/source/repos/cpp/vcpkg/installed/x86-windows/lib)
target_link_libraries(raylib-demo PRIVATE raylib)

if (CMAKE_CXX_COMPILER_ID MATCHES "Clang|AppleClang|GNU")
    target_compile_options(raylib-demo PRIVATE -Wall -Wextra -Wunreachable-code -Wpedantic)
endif()
if (CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    target_compile_options(raylib-demo PRIVATE -Wweak-vtables -Wexit-time-destructors -Wglobal-constructors -Wmissing-noreturn )
endif()
if (CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
    target_compile_options(raylib-demo PRIVATE /W4 /w44265 /w44061 /w44062 )
endif()