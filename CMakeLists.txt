cmake_minimum_required(VERSION 3.16)

project(student_information_system
    VERSION 0.1.0
    LANGUAGES CXX
)

# C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Export compile commands (useful for tooling)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Core library
add_library(sis_core
    src/app.cpp
)

target_include_directories(sis_core
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
)

# Main application
add_executable(sis_app
    src/main.cpp
)

target_link_libraries(sis_app
    PRIVATE sis_core
)


# Tests (optional)
option(BUILD_TESTS "Build tests" ON)

if(BUILD_TESTS)
    enable_testing()

    add_executable(test_basic
        tests/test_basic.cpp
    )

    target_link_libraries(test_basic
        PRIVATE sis_core
    )

    add_test(NAME basic_test COMMAND test_basic)
endif()
