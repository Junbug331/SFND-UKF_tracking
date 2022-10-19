cmake_minimum_required(VERSION 3.11 FATAL_ERROR)
set(CMAKE_CXX_STANDARD 14)

project(ukf-highway)
set(TARGET ${PROJECT_NAME})

add_definitions(-DDATA_PATH="${CMAKE_CURRENT_SOURCE_DIR}/sensor_data/pcd")
add_compile_options(-Wall -O3)

add_subdirectory(UKF)

add_executable (${TARGET}
    src/main.cpp
)

target_link_libraries (${TARGET} PRIVATE
    UKF
)
