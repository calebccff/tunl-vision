cmake_minimum_required(VERSION 3.10)
project(tunl-vision CXX)

set(CXX_STANDARD 17)

file(GLOB SOURCES "*.cpp")
file(GLOB HEADERS "../include/*.h")

find_package(libdatachannel CONFIG REQUIRED)
target_link_libraries(main PRIVATE LibDatachannel::datachannel)

add_library(tunl-vision ${SOURCES})

set_target_properties(tunl-vision PROPERTIES PUBLIC_HEADER "${HEADERS}")
target_include_directories(tunl-vision
	PUBLIC
	$<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include>
	$<INSTALL_INTERFACE:include>)

install(TARGETS tunl-vision
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
	PUBLIC_HEADER DESTINATION include/)