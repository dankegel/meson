cmake_minimum_required(VERSION 3.5)

project(cmMod)
set (CMAKE_CXX_STANDARD 14)

add_definitions("-DDO_NOTHING_JUST_A_FLAG=1")

add_library(cmModLib SHARED cmMod.cpp)
include(GenerateExportHeader)
generate_export_header(cmModLib)
