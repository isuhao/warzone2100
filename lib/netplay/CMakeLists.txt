cmake_minimum_required (VERSION 3.5)

file(GLOB HEADERS "*.h")
file(GLOB SRC "*.cpp")

find_package (Threads REQUIRED)

add_library(netplay STATIC ${HEADERS} ${SRC})
target_link_libraries(netplay PRIVATE framework libminiupnpc-static)
if("${CMAKE_CXX_COMPILER_ID}" MATCHES "GNU")
	target_link_libraries(netplay PRIVATE pthread)
endif()
target_link_libraries(netplay PRIVATE Threads::Threads)
