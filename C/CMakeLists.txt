add_library(C C.cpp)

target_compile_definitions(C
    INTERFACE Clib_USER
    PRIVATE Clib_INNER
)

add_library(${PROJECT_NAME}::C ALIAS C)

target_link_libraries(C
        PUBLIC H)

target_include_directories(C PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
)