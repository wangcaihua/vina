cmake_minimum_required(VERSION 3.19)
project(vina)

set(CMAKE_CXX_STANDARD 11)

set(BOOST_ROOT "/usr/local/Cellar/boost/1.76.0")
find_package(Boost 1.76.0 COMPONENTS system filesystem thread program_options REQUIRED)

if(NOT Boost_FOUND)
    message(FATAL_ERROR "Could not find boost!")
else()
    message("Boost_INCLUDE_DIRS: ${Boost_INCLUDE_DIRS}")
    message("Boost_LIBRARIES: ${Boost_LIBRARIES}")
    message("Boost_VERSION: ${Boost_VERSION}")
    include_directories(${Boost_INCLUDE_DIR})
endif()

file(GLOB SRCS lib/*.h lib/*.cpp)
add_executable(vina main.cpp ${SRCS})
target_link_libraries(vina ${Boost_LIBRARIES})
