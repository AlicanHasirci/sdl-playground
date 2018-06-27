cmake_minimum_required(VERSION 3.10)
project(sdl-playground)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

file(GLOB_RECURSE SOURCES "src/*.cpp")
file(GLOB_RECURSE HEADERS "inc/*.h")
add_executable(${PROJECT_NAME} main.cpp ${SOURCES} ${HEADERS})

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(SDL2_ttf REQUIRED)

find_package(GLEW REQUIRED)
find_package(GLM REQUIRED)

include_directories(
        ${SDL2_INCLUDE_DIR}
        ${SDL2_IMAGE_INCLUDE_DIR}
        ${SDL2_TTF_INCLUDE_DIR}
        ${GLEW_INCLUDE_DIRECTORIES}
        ${GLM_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME}
        "-framework OpenGL"
        ${SDL2_LIBRARY}
        ${SDL2_IMAGE_LIBRARY}
        ${SDL2_TTF_LIBRARY}
        ${GLEW_LIBRARIES}
        ${GLM_LIBRARY_DIRS})

#get_cmake_property(_variableNames VARIABLES)
#list (SORT _variableNames)
#foreach (_variableName ${_variableNames})
#    message(STATUS "${_variableName}=${${_variableName}}")
#endforeach()