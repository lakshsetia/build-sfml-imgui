cmake_minimum_required(VERSION 3.27)

project(build-sfml-imgui)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

set(DEPENDENCIES "${CMAKE_CURRENT_SOURCE_DIR}/dependencies")

# add SFML Dependency
if(preset_vs)
    set(SFML_DEPENDENCIES "${DEPENDENCIES}/sfml/sfml_vs")
elseif(preset_make)
    set(SFML_DEPENDENCIES "${DEPENDENCIES}/sfml/sfml_make")
endif()
set(SFML_STATIC_LIBRARIES TRUE)
set(Ogg_DIR "${SFML_DEPENDENCIES}/lib/cmake/Ogg")
set(SFML_DIR "${SFML_DEPENDENCIES}/lib/cmake/SFML")
find_package(SFML 3 REQUIRED COMPONENTS Window System Audio Graphics)

# add ImGui Dependency
# add_subdirectory(${DEPENDENCIES}/imgui)
set(IMGUI_DIR "${DEPENDENCIES}/imgui" CACHE STRING "path to ImGui directory containing imgui.h and other files")

# add ImGui::SFML Dependency
add_subdirectory(${DEPENDENCIES}/imgui-sfml)

# add source files
file(GLOB SOURCE_FILES
    "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h"
)

# add executable 
add_executable(${PROJECT_NAME} ${SOURCE_FILES})

# link libraries and include directories
target_link_libraries(${PROJECT_NAME} PRIVATE SFML::Window SFML::System SFML::Audio SFML::Graphics)

target_link_libraries(${PROJECT_NAME} PRIVATE ImGui-SFML)