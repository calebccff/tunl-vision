cmake_minimum_required(VERSION 3.0)
project(TunlVision)
set(CMAKE_BUILD_TYPE Release)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -Wno-unused-parameter -Werror")

include_directories(${CMAKE_SOURCE_DIR}/include)

add_subdirectory(lib)

find_package(libdatachannel CONFIG REQUIRED)

add_executable(TunlVision TunlVision.cpp)
target_link_libraries(TunlVision tunl-vision)
target_link_libraries(main PRIVATE LibDatachannel::datachannel)
install(TARGETS TunlVision DESTINATION bin)
