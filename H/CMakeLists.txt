add_library(H INTERFACE)

target_include_directories(H INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>)
