
project(FitzComm)
cmake_minimum_required(VERSION 3.3)

include(conanbuildinfo.cmake)
conan_basic_setup()

#gather our files
FILE (GLOB SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cc)
FILE (GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/FitzComm/*.h)

#build the executable
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include
                    ${CMAKE_CURRENT_SOURCE_DIR}/include/FitzComm #needed for generated proto-files
                    ${CONAN_INCLUDE_DIRS})
add_library (FitzComm STATIC ${SOURCES} ${HEADERS})
target_link_libraries(FitzComm ${CONAN_LIBS})

install(FILES ${HEADERS}
        DESTINATION E:/Github/Fitznet/install/include/FitzComm)
        
install(FILES ${SOURCES}
        DESTINATION E:/Github/Fitznet/install/sources/FitzComm)
