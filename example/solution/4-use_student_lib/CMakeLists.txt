cmake_minimum_required(VERSION 3.5)

project(TestStudentLib)

# Generate executable.
add_executable(TestStudentLib test.cpp)

# Include directory with header files.
target_include_directories(TestStudentLib PUBLIC ../3-student_lib/src)

# Set library version to use.
set(LIB_VERSION "1.0" CACHE STRING "Library version to use.")

if(${LIB_VERSION} STREQUAL "2.0")
  # Define preprocessor macro.
  target_compile_definitions(TestStudentLib PRIVATE STUDENT_VERSION_2)

  # Link to proper library version.
  target_link_libraries(TestStudentLib /FULL/PATH/TO/example_cmake/solution/3-student_lib/build/libstudent.so.2.0)
else()
  target_link_libraries(TestStudentLib /FULL/PATH/TO/example_cmake/solution/3-student_lib/build/libstudent.so.1.0)
endif()

# WARNING: modify LD_LIBRARY_PATH accordingly before execution, or pass a proper "-Wl,-rpath" flag.
