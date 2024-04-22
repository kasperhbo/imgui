cmake_minimum_required(VERSION 3.28)
project(imgui-vulkan)
set(CMAKE_CXX_STANDARD 23)

if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Debug CACHE STRING "" FORCE)
endif ()

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DVK_PROTOTYPES")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DVK_PROTOTYPES")

#function that returns the name of the project
function(get_project_name)
    return(${CMAKE_PROJECT_NAME})
endfunction()

function(get_project_exe_name)
    return(${CMAKE_PROJECT_NAME}_exe)
endfunction()

function(get_project_lib_name)
    return(${CMAKE_PROJECT_NAME}_lib)
endfunction()

function(get_project_public_include_path)
    return(${CMAKE_CURRENT_SOURCE_DIR}/public/include)
endfunction()

function(get_project_private_include_path)
    return(${CMAKE_CURRENT_SOURCE_DIR}/public/include)
endfunction()

function(get_project_sources_dir)
    return(${CMAKE_CURRENT_SOURCE_DIR}/sources/)
endfunction()



#imgui-vulkan
set(IMGUI_SOURCES_COPY
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${get_project_sources_dir}/backends/imgui_impl_vulkan.cpp
    ${get_project_sources_dir}/backends/imgui_vulkan_wrapper.cpp
    ${get_project_sources_dir}/imgui.cpp
    ${get_project_sources_dir}/imgui_draw.cpp
    ${get_project_sources_dir}/imgui_demo.cpp
    ${get_project_sources_dir}/imgui_tables.cpp
    ${get_project_sources_dir}/imgui_widgets.cpp
)

set(IMGUI-VULKAN-SOURCES
        ${get_project_sources_dir}/backends/imgui_impl_glfw.cpp
        ${get_project_sources_dir}/backends/imgui_impl_vulkan.cpp
        ${get_project_sources_dir}/backends/imgui_vulkan_wrapper.cpp
        ${get_project_sources_dir}/imgui.cpp
        ${get_project_sources_dir}/imgui_draw.cpp
        ${get_project_sources_dir}/imgui_demo.cpp
        ${get_project_sources_dir}/imgui_tables.cpp
        ${get_project_sources_dir}/imgui_widgets.cpp
)

add_library(${get_project_lib_name} STATIC)
# Dear ImGui
target_include_directories(${EXE_NAME}
        PRIVATE
        ${IMGUI_DIR}
        ${IMGUI_DIR}/backends)
target_include_directories(${EXE_NAME}
        public)




