cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_STANDARD 14)
project(UKF)
set(LIB_NAME ${PROJECT_NAME})

add_library(${LIB_NAME}
   highway.cpp
   render.cpp
   tools.cpp
   ukf.cpp
)

# PCL Library
find_package(PCL REQUIRED)
if (PCL_FOUND)
    message(STATUS "PCL(${PCL_VERSION}) Found! - ${PCL_DIR}")
endif()

add_definitions(${PCL_DEFINITIONS})

target_include_directories(${LIB_NAME} PUBLIC
    include
    ${PCL_INCLUDE_DIRS}
)

target_link_directories(${LIB_NAME} PUBLIC
    ${PCL_LIBRARY_DIRS}
)

target_link_libraries(${LIB_NAME} PUBLIC
    ${PCL_LIBRARIES}
    stdc++fs
)


