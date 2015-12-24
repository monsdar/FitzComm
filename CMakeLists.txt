cmake_minimum_required(VERSION 3.3)

#find the needed thirdparty
set (PROTO_INCLUDES "E:/Github/protobuf-2.6.1/src" CACHE PATH "Sets the path to the Protobuf includes")
set (PROTO_STATIC_LIBRARY "E:/Github/protobuf-2.6.1/vsprojects/Release/libprotobuf.lib" CACHE PATH "Sets the path to the Protobuf static library")

#gather our files
FILE (GLOB SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cc)
FILE (GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/FitzComm/*.h)

#build the executable
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include 
                    ${PROTO_INCLUDES})
add_library (FitzComm STATIC ${SOURCES} ${HEADERS})
target_link_libraries(FitzComm ${PROTO_LIBRARY})

install(TARGETS FitzComm
        DESTINATION E:/Github/Fitznet/install/lib)
        
install(FILES ${HEADERS}
        DESTINATION E:/Github/Fitznet/install/include/FitzComm)
