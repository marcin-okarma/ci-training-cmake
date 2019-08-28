add_subdirectory(B)

add_library(A A.cpp)

add_library(${PROJECT_NAME}::A ALIAS A)

target_link_libraries(A
        PUBLIC Ba)

target_include_directories(A PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
)