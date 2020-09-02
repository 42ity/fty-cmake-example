cmake_minimum_required(VERSION 3.13)
cmake_policy(VERSION 3.13)

project(hello
    VERSION 1.0.0
)

##############################################################################################################
find_package(fty-cmake PATHS ${CMAKE_BINARY_DIR}/fty-cmake)
##############################################################################################################

#Create a shared library for "hello" (libhello)

etn_target(shared ${PROJECT_NAME}
    SOURCES
        src/*.cpp
    INCLUDE_DIRS
        src
    PUBLIC_INCLUDE_DIR
        public_includes
    PUBLIC
        hello/hello.h
)

if(BUILD_TESTING)
    enable_testing()

    # Create a target for the tests
    etn_test(${PROJECT_NAME}-test
        SOURCES
            tests/*.cpp
        USES
        ${PROJECT_NAME}
        Catch2::Catch2 
    )
    
endif()