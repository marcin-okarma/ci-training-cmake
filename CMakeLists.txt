cmake_minimum_required(VERSION 3.15)
project(cmake_training)

# -----------------------------------  comment this to start test

add_definitions("--std=c++11")

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/A)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/A/B)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/C)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/H)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/D)

add_executable(ATest
        C/C.cpp
        A/A.cpp
        A/B/Ba.cpp
        A/B/Bb.cpp
        D/D.cpp
        ATest.cpp
)

add_executable(CTest
        C/C.cpp
        A/A.cpp
        A/B/Ba.cpp
        A/B/Bb.cpp
        D/D.cpp
        CTest.cpp
)

add_executable(DTest
        C/C.cpp
        A/A.cpp
        A/B/Ba.cpp
        A/B/Bb.cpp
        D/D.cpp
        DTest.cpp
)

file(WRITE DATE/BuildTime.h "#define BUILD_TIME \"test\"")
add_executable(DATETest
        DATETest.cpp
)

# -----------------------------------  comment this to start test - end of section


# -----------------------------------  uncomment this to start test
#add_subdirectory(A)
#add_subdirectory(H)
#add_subdirectory(C)
#add_subdirectory(D)
#add_executable(ATest ATest.cpp)
#target_link_libraries(ATest
#        PRIVATE ${PROJECT_NAME}::A
#        PRIVATE ${PROJECT_NAME}::C
#        PRIVATE ${PROJECT_NAME}::D
#)
#
#add_executable(CTest CTest.cpp)
#target_link_libraries(CTest
#        PRIVATE ${PROJECT_NAME}::C
#)
#
#add_executable(DTest DTest.cpp)
#target_link_libraries(DTest
#        PRIVATE ${PROJECT_NAME}::D
#)
#add_executable(DATETest DATETest.cpp)
# -----------------------------------  uncomment this to start test - end of section

enable_testing()
include(CTest)

add_test(NAME ATest COMMAND ./ATest)
add_test(NAME CTest COMMAND ./CTest)
add_test(NAME DTest COMMAND ./DTest)
add_test(NAME DATETest COMMAND ./DATETest == `date -I`)