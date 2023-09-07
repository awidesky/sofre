cmake_minimum_required( VERSION 3.8 )

project( sofre )

find_package( OpenGL REQUIRED )

set(GLFW_ROOT_DIR "${PROJECT_SOURCE_DIR}/glfw")
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE )
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE )
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE )

add_subdirectory( glfw )


set(ALL_INCLUDES
	"${PROJECT_SOURCE_DIR}/include"
	"${PROJECT_SOURCE_DIR}/glfw/include"
)

set(ALL_LIBS
	"glfw"
)


set(SRCFILES
	src/KHR/khrplatform.h
	src/glad/glad.h
	src/glad.c
	src/core.hpp
	src/sofre.cpp
)

set(HEADERS
	include/sofre/sofre.hpp
)

add_library(sofre ${SRCFILES} ${HEADERS})

target_include_directories(sofre PUBLIC ${ALL_INCLUDES})
target_include_directories(sofre PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src)
	
target_link_libraries(sofre ${ALL_LIBS})

