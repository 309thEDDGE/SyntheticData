cmake_minimum_required(VERSION 3.15)

project(SynthCh10Gen)

option(COMPILE_NASA "compile with NASA data" ON)

if(CMAKE_SOURCE_DIR STREQUAL PROJECT_SOURCE_DIR)
     # I am top-level project.
    find_library(LIBSQLITE3 NAMES libsqlite3 sqlite3 libsqlite3.so)

    add_subdirectory(../3rdParty ./libs)
endif()


add_executable(synth_ch10gen
    Ch10Format_1553.cpp
    Ch10Format_1553_Nav.cpp
    Ch10Format_A429_AR100.cpp
    Ch10Format_A429.cpp
    Ch10Format_PCM.cpp
    Ch10Writer_1553.cpp
    Ch10Writer_A429.cpp
    Ch10Writer_Index.cpp
    Ch10Writer_PCM.cpp
    Ch10Writer_Time.cpp
    Ch10Writer_Video.cpp
    Source_BMNavDB.cpp
    Source_BMNavTxt.cpp
    Source_NasaNavTxt.cpp
    Source_VideoDB.cpp
    Source_CsvTxt.cpp
    SynthCh10Gen.cpp)

if (COMPILE_NASA)
    target_compile_definitions(synth_ch10gen PUBLIC COMPILE_NASA)
endif()

target_link_libraries(synth_ch10gen PUBLIC irig106 csvparser)
target_link_libraries(synth_ch10gen PUBLIC ${LIBSQLITE3})
