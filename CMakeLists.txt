cmake_minimum_required(VERSION 3.18)
project(copy-file VERSION 1.0 DESCRIPTION "testing copy file if modified on make all")
set(FILE_PATH "some_dir/file.txt")
add_executable(hello hello.c)
#add_custom_command(
#    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/${FILE_PATH}
#    COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_CURRENT_SOURCE_DIR}/${FILE_PATH} ${CMAKE_CURRENT_BINARY_DIR}/${FILE_PATH}
#    MAIN_DEPENDENCY ${CMAKE_CURRENT_SOURCE_DIR}/${FILE_PATH})
add_custom_command(
    TARGET hello
    POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy
          ${CMAKE_CURRENT_SOURCE_DIR}/${FILE_PATH} ${CMAKE_CURRENT_BINARY_DIR}/${FILE_PATH})
#configure_file(${FILE_PATH} ${FILE_PATH} COPYONLY)
