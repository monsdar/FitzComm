cmake_minimum_required(VERSION 3.3)

#find the needed thirdparty
set (PROTO_INCLUDES "E:/Github/protobuf-2.6.1/src" CACHE PATH "Sets the path to the Protobuf includes")
set (PROTO_STATIC_LIBRARY "E:/Github/protobuf-2.6.1/vsprojects/x64/Release/libprotobuf.lib" CACHE PATH "Sets the path to the Protobuf static library")

#gather our files
FILE (GLOB SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cc)
FILE (GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/FitzComm/*.h)

#build the executable
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include
                    ${CMAKE_CURRENT_SOURCE_DIR}/include/FitzComm #needed for generated proto-files
                    ${PROTO_INCLUDES})
add_library (FitzComm STATIC ${SOURCES} ${HEADERS})
target_link_libraries(FitzComm ${PROTO_LIBRARY})

install(FILES ${HEADERS}
        DESTINATION E:/Github/Fitznet/install/include/FitzComm)
        
install(FILES ${SOURCES}
        DESTINATION E:/Github/Fitznet/install/sources/FitzComm)
