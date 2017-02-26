cmake_minimum_required(VERSION 3.5)
project(vulkantest)

set(CMAKE_CXX_STANDARD 11)

include_directories(/usr/include)
link_libraries(/usr/lib/x86_64-linux-gnu/libxcb.so)
add_definitions(-DVK_USE_PLATFORM_XCB_KHR)

FILE(TO_NATIVE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/lunarg.ppm LUNARG)

include_directories(
        ~/openvr-1.0.6/headers/
        ~/VulkanSDK/1.0.39.1/x86_64/include/
        ~/VulkanSDK/1.0.39.1/examples/
)

link_directories(
        ~/openvr-1.0.6/bin/linux64/
        ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu
        ~/VulkanSDK/1.0.39.1/x86_64/lib/
)

LINK_LIBRARIES(
        vulkan
        openvr_api
)

set(SOURCE_FILES
        main.cpp
        Matrices.cpp
)
add_executable(vulkantest ${SOURCE_FILES})
