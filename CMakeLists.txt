cmake_minimum_required(VERSION 3.18)
project(copy-file VERSION 1.0 DESCRIPTION "testing copy file if modified on make all")
set(FILE_PATH "some_dir/file.txt")
add_executable(hello hello.c)
add_custom_target(copy ALL)
add_custom_command(
    TARGET copy
    PRE_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
        ${CMAKE_CURRENT_SOURCE_DIR}/${FILE_PATH} ${CMAKE_CURRENT_BINARY_DIR}/${FILE_PATH})