# create varibale SOURCE_FILES for all .cpp and .h files
file(GLOB SOURCE_FILES
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
)

# make ImGui library
add_library(ImGui ${SOURCE_FILES})

# add include dir to library
target_include_directories(ImGui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})