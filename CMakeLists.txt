cmake_minimum_required( VERSION 3.8 )

project( sofre )

find_package( OpenGL REQUIRED )

set(GLFW_ROOT_DIR "${PROJECT_SOURCE_DIR}/glfw")
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE )
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE )
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE )

set(glew-cmake_BUILD_STATIC ON CACHE BOOL "" FORCE )
set(glew-cmake_BUILD_SHARED OFF CACHE BOOL "" FORCE )


add_subdirectory( glfw )
add_subdirectory( glew )


set(ALL_INCLUDES
	"${PROJECT_SOURCE_DIR}/include"
	"${PROJECT_SOURCE_DIR}/glew/include"
	"${PROJECT_SOURCE_DIR}/glfw/include"
)

set(ALL_LIBS
	"glfw"
	"libglew_static"
)


set(SRCFILES
	src/sofre.cpp
)

set(HEADERS
	include/sofre/sofre.hpp
)

#AUX_SOURCE_DIRECTORY(${CMAKE_CURRENT_SOURCE_DIR}/src SRCFILES)

add_library(sofre ${SRCFILES} ${HEADERS})

target_include_directories(sofre PRIVATE ${ALL_INCLUDES})
target_include_directories(sofre PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
	
target_link_libraries(sofre ${ALL_LIBS})

