project(cmake_example_c)
cmake_minimum_required(VERSION 3.0)

set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

if(MSVC)
else()
    set(CMAKE_C_FLAGS_DEBUG "-O0 -g")
    set(CMAKE_C_FLAGS_RELEASE "-W -Wall -O3")
endif()

if(MSVC)
    #    include_directories("C:/xxx/include")
    #    link_directories("C:/xxx/lib")
else()
    include_directories(/usr/include /usr/local/include)
    link_directories(/usr/lib /usr/local/lib)
endif()

#file(GLOB_RECURSE SRCS src/*.c)
file(GLOB SRCS src/*.c)
add_executable(test_program_c ${SRCS})
if(MSVC)
    #    target_link_libraries(test_program aaa.lib bbb.lib)
else()
    #    target_link_libraries(test_program aaa bbb)
endif()

