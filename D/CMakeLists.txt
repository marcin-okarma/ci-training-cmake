add_library(D D.cpp)

add_library(${PROJECT_NAME}::D ALIAS D)

target_link_libraries(D
        PUBLIC C
        PUBLIC Bb)

target_include_directories(D PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
)
