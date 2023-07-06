cmake_minimum_required(VERSION 3.6 FATAL_ERROR)
project(my_project LANGUAGES CXX)

# Using C17 and C++20
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Use wxWidgets static libraries
set(wxWidgets_USE_STATIC 1)
set(wxBUILD_SHARED OFF)

# Include fetch content module
include(FetchContent)

FetchContent_Declare(
    wxWidgets
    GIT_REPOSITORY
    https://github.com/wxWidgets/wxWidgets.git
    GIT_TAG
    v3.1.4
    )
    
FetchContent_GetProperties(wxWidgets)

if(NOT wxWidgets_POPULATED)
    FetchContent_Populate(wxWidgets)
    add_subdirectory(${wxwidgets_SOURCE_DIR} ${wxwidgets_BUILD_DIR})
endif()

set(HEADERS ${CMAKE_CURRENT_LIST_DIR}/include/*.h)
set(SOURCES ${CMAKE_CURRENT_LIST_DIR}/source/*.cpp)

add_executable(main WIN32 ${SOURCES} ${HEADERS})

target_include_directories(main PRIVATE ${wxwidgets_SOURCE_DIR}/include)
target_link_libraries(main PRIVATE wx::base wx::core)