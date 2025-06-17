cmake_minimum_required(VERSION 3.31)
project(advent-of-code-cpp LANGUAGES CXX)  # Change project name!

# =============== Core Settings ===============
set(CMAKE_CXX_STANDARD 23)                # Use C++17 (or 20/23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)       # Enforce standard
set(CMAKE_CXX_EXTENSIONS OFF)             # Disable compiler extensions
set(CMAKE_VERBOSE_MAKEFILE ON)

# =============== Warnings as Errors ===============
if (MSVC)
    add_compile_options(/W4 /WX)          # MSVC: max warnings + errors
else()
    add_compile_options(-Wall -Wextra -Wpedantic -Werror)  # GCC/Clang
    add_compile_options(-Wshadow -Wnon-virtual-dtor)       # Extra warnings
endif()

# =============== Executable ===============
add_executable(${PROJECT_NAME}
        src/2015/day01/main.cpp
        #src/add.cpp
        # Add more sources here: src/core/module.cpp
)

# =============== Include Directories ===============
target_include_directories(${PROJECT_NAME} PRIVATE
        include/
)

# =============== Optional: Unit Testing ===============
#if (BUILD_TESTING)
#    enable_testing()
#    add_subdirectory(tests)  # Requires a CMakeLists.txt in tests/
#endif()

# =============== Optional: Generate compile_commands.json ===============
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)  # For clang-tidy, clangd, etc.