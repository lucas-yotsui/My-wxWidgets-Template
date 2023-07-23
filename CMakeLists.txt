cmake_minimum_required(VERSION 3.11 FATAL_ERROR)
project(my_project LANGUAGES CXX)

# Using C++20
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Use wxWidgets static libraries
set(wxWidgets_USE_STATIC ON)
set(wxBUILD_SHARED OFF)

# Include FetchContent module
include(FetchContent)

# Fetch wxWidgets dependency statement declaration
FetchContent_Declare(
    wxWidgets
    SYSTEM
    GIT_REPOSITORY
        https://github.com/wxWidgets/wxWidgets.git
    GIT_TAG
        v3.1.4
)

# Message to inform user that script is not bugged, just busy resolving dependecy
message(STATUS "Baixando wxWidgets e incluindo-o no projeto")

# Effectively fetch wxWidgets dependency
FetchContent_MakeAvailable(wxWidgets)

# Include all of the program's header and source files
file(GLOB_RECURSE HEADERS ${CMAKE_CURRENT_LIST_DIR}/include/*.h)
file(GLOB_RECURSE SOURCES 
        ${CMAKE_CURRENT_LIST_DIR}/source/*.cpp
        ${CMAKE_CURRENT_LIST_DIR}/source/*.c
    )

# Configure the project to look for include files in the 'include' directory
include_directories(${CMAKE_CURRENT_LIST_DIR}/include)
# Configure the project to look for include files in the 'assets' directory (where xpm files live) 
include_directories(SYSTEM ${CMAKE_CURRENT_LIST_DIR}/assets)

# Create program executable and link against all of the program's header and source files
add_executable(${PROJECT_NAME} ${SOURCES} ${HEADERS})

# Link wxWidgets libraries against program executable
target_include_directories(${PROJECT_NAME} PRIVATE ${wxwidgets_SOURCE_DIR}/include)
target_link_libraries(${PROJECT_NAME} PRIVATE wx::base wx::core)

# Set compiler warnings and make them be treated as errors
set_target_properties(${PROJECT_NAME} PROPERTIES
    COMPILE_OPTIONS "-Wall;-Wextra;-pedantic;-Werror"
)