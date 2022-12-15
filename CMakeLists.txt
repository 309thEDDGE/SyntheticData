cmake_minimum_required(VERSION 3.16)
project(synthetic-data)

find_library(LIBSQLITE3 NAMES libsqlite3 sqlite3 libsqlite3.so)

add_subdirectory(3rdParty)
add_subdirectory(BM6toDB)
add_subdirectory(SynthCh10Gen)

