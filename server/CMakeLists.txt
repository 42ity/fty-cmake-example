cmake_minimum_required(VERSION 3.13)
cmake_policy(VERSION 3.13)

project(hello-server
    VERSION 1.0.0
)

##############################################################################################################
find_package(fty-cmake PATHS ${CMAKE_BINARY_DIR}/fty-cmake)
##############################################################################################################

#Create a an exacutable for "using "hello" shared library (hello-server)

etn_target(exe ${PROJECT_NAME}
    SOURCES
        src/*.cpp
    USES
        hello
)
