cmake_minimum_required(VERSION 3.26)
project(AdvancedTooling2024)

set(CMAKE_CXX_STANDARD 17)
file(GLOB_RECURSE SOURCES
        mge/*.h
        mge/*.cpp
)

add_executable(AdvancedTooling2024 ${SOURCE_FILES} ${SOURCES}
        glm.hpp main.cpp)
find_package(SFML COMPONENTS system window graphics CONFIG REQUIRED)
target_link_libraries(AdvancedTooling2024 PRIVATE sfml-system sfml-network sfml-graphics sfml-window)
find_package(GLEW REQUIRED)
target_link_libraries(AdvancedTooling2024 PRIVATE GLEW::glew)

file(MAKE_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/mge")
file(COPY mge/shaders DESTINATION "${CMAKE_CURRENT_BINARY_DIR}/mge")
file(COPY mge/textures DESTINATION "${CMAKE_CURRENT_BINARY_DIR}/mge")
file(COPY mge/models DESTINATION "${CMAKE_CURRENT_BINARY_DIR}/mge")
file(COPY mge/fonts DESTINATION "${CMAKE_CURRENT_BINARY_DIR}/mge")
