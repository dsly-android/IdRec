cmake_minimum_required(VERSION 3.4.1)

include_directories(src/main/cpp/include)
#编译源文件
file(GLOB my_source_path  src/main/cpp/*.cpp src/main/cpp/*.c)
add_library( native-lib SHARED ${my_source_path} )

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -L${CMAKE_SOURCE_DIR}/src/main/jniLibs/armeabi-v7a")

target_link_libraries( # Specifies the target library.
        native-lib

        log
        jnigraphics
        ${CMAKE_SOURCE_DIR}/src/main/jniLibs/armeabi-v7a/libopencv_java3.so)