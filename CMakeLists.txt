cmake_minimum_required(VERSION 3.20)

project(imagify
    VERSION 1.0
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS ON)

add_compile_options(-Wall
    -Wextra
    -Wunused-variable
    -Wunused-function
    -Wpedantic
    -Wshadow
    -Wconversion
    -Wsign-conversion
)

find_package(OpenCV 4 REQUIRED)

file(GLOB_RECURSE PROJECT_SOURCES
    CONFIGURE_DEPENDS
    src/domain/*.cpp
    src/app/*.cpp
    src/process/*.cpp
)

include_directories(${PROJECT_NAME}
    PRIVATE
        include
)

add_executable(${PROJECT_NAME}
    ${PROJECT_SOURCES}
)

# Include OpenCV headers
target_include_directories(${PROJECT_NAME}
    PRIVATE
        ${OpenCV_INCLUDE_DIRS}
)

# Link OpenCV libraries
target_link_libraries(${PROJECT_NAME}
    PRIVATE
        ${OpenCV_LIBS}
)
