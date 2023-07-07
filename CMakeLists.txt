cmake_minimum_required(VERSION 3.11 FATAL_ERROR)
project(my_project LANGUAGES CXX)

# Using C++20
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Use wxWidgets static libraries
set(wxWidgets_USE_STATIC 1)
set(wxBUILD_SHARED OFF)

# Include FetchContent module
include(FetchContent)

# Fetch wxWidgets dependency statement declaration
FetchContent_Declare(
    wxWidgets
    GIT_REPOSITORY
        https://github.com/wxWidgets/wxWidgets.git
    GIT_TAG
        v3.1.4
)

# Message to inform user that script is not bugged, just busy resolving dependecy
message(STATUS "Baixando wxWidgets e incluindo-o no projeto")

# Effectively fetch wxWidgets dependency
FetchContent_GetProperties(wxWidgets)

if(NOT wxWidgets_POPULATED)
FetchContent_Populate(wxWidgets)
add_subdirectory(${wxwidgets_SOURCE_DIR} ${wxwidgets_BUILD_DIR})
endif()

# Include all of the program's header and source files
file(GLOB_RECURSE HEADERS ${CMAKE_CURRENT_LIST_DIR}/include/*.h)
file(GLOB_RECURSE SOURCES ${CMAKE_CURRENT_LIST_DIR}/source/*.cpp)

# Create program executable and link against all of the program's header and source files
add_executable(${PROJECT_NAME} ${SOURCES} ${HEADERS})

# Link wxWidgets libraries against program executable
target_include_directories(${PROJECT_NAME} PRIVATE ${wxwidgets_SOURCE_DIR}/include)
target_link_libraries(${PROJECT_NAME} PRIVATE wx::base wx::core)

# Copy all assets to build directory to make them available to the program
add_custom_target(copy_assets
    COMMAND ${CMAKE_COMMAND} -E copy_directory ${CMAKE_CURRENT_LIST_DIR}/assets ${CMAKE_CURRENT_BINARY_DIR}/assets
)
add_dependencies(${PROJECT_NAME} copy_assets)