PROJECT(lockstep)
cmake_minimum_required(VERSION 2.8)
INCLUDE_DIRECTORIES(.)
INCLUDE_DIRECTORIES(./khaki)
INCLUDE_DIRECTORIES(./khaki/deps/include)
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=c++11 -pthread")
MESSAGE(${CMAKE_CURRENT_SOURCE_DIR})
LINK_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/./khaki/build)
LINK_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/./khaki/deps/lib)

AUX_SOURCE_DIRECTORY(. SRC_CPP)
AUX_SOURCE_DIRECTORY(./proto SRC_CPP_PROTO)
ADD_EXECUTABLE(lockstep ${SRC_CPP} ${SRC_CPP_PROTO})

TARGET_LINK_LIBRARIES(lockstep libkhaki.a)
TARGET_LINK_LIBRARIES(lockstep liblog4cpp.a)
TARGET_LINK_LIBRARIES(lockstep libprotobuf.a)