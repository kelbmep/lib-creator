# CMakeList.txt: проект CMake для LibrariesCreator; включите исходный код и определения,
# укажите здесь логику для конкретного проекта.
#
cmake_minimum_required (VERSION 3.8)

# Добавьте источник в исполняемый файл этого проекта.

#HeaderOnly
add_library(HeaderOnlyLibrary INTERFACE Sum.ipp)
set_target_properties(HeaderOnlyLibrary PROPERTIES PUBLIC_HEADER Sum.ipp)

install(TARGETS HeaderOnlyLibrary
        PUBLIC_HEADER
        DESTINATION ${CMAKE_SOURCE_DIR}/HeaderOnlyLibrary/include
        )

#Static
add_library(StaticLibrary STATIC Mult.cpp Mult.hpp)
set_target_properties(StaticLibrary PROPERTIES PUBLIC_HEADER Mult.hpp)

install(TARGETS StaticLibrary
        PUBLIC_HEADER DESTINATION ${CMAKE_SOURCE_DIR}/StaticLibrary/include
        ARCHIVE DESTINATION ${CMAKE_SOURCE_DIR}/StaticLibrary/lib
        )

#Dynamic
add_library(DynamicLibrary SHARED Diff.cpp Diff.hpp)
set_target_properties(DynamicLibrary PROPERTIES PUBLIC_HEADER Diff.hpp)

install(TARGETS DynamicLibrary
        PUBLIC_HEADER DESTINATION ${CMAKE_SOURCE_DIR}/DynamicLibrary/include
        ARCHIVE DESTINATION ${CMAKE_SOURCE_DIR}/DynamicLibrary/lib
        RUNTIME DESTINATION ${CMAKE_SOURCE_DIR}/DynamicLibrary/lib
        )
