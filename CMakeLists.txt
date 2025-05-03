# Запуск
# conan install path/to/conan/file --output-folder=build --build=missing
# 
# conan install /home/eduard/Projects/iu7/CPP_v1/2.cmake-conan/conanfile-example.txt -of /home/eduard/Projects/iu7/CPP_v1/2.cmake-conan/build-conan --build=missing
# cd build
# 
# source conanbuild.sh  - необязательный элемент
# 
# cmake .. -DCMAKE_TOOLCHAIN_FILE=conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release        - .. значит что файл cmakelists.txt лежит на директорию выше
# cmake --build .
# 
# source deactivate_conanbuild.sh
# 
# ./timer

# vscode .vscode/c_cpp_properties.json    - чтобы vscode не подчеркивал
# {
#     "configurations": [
#         {
#             "name": "Linux",
#             "includePath": [
#                 "${workspaceFolder}/**",
#                 "~/.conan2/**"
#             ],
#             "intelliSenseMode": "linux-gcc-x64",
#             "compilerPath": "/usr/bin/g++"
#         }
#     ],
#     "version": 4
# }

cmake_minimum_required(VERSION 3.16)

# project name
project(CG-project)

#standart
set(CMAKE_CXX_STANDARD 17)

#compiler flags
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

#search glad in conan
include(${PROJECT_SOURCE_DIR}/build-conan/conan_toolchain.cmake)
find_package(glad)

add_executable(${PROJECT_NAME} main.cpp)

#added libraries
target_link_libraries(${PROJECT_NAME} glfw glad::glad)