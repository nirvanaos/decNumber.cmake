cmake_minimum_required(VERSION 3.15)
project(decNumber VERSION 3.68 LANGUAGES C)
cmake_policy(SET CMP0010 NEW)
set(CMAKE_CONFIGURATION_TYPES Debug Release)

add_library(decNumber
    decNumber/decContext.c
    decNumber/decDouble.c
    decNumber/decNumber.c
    decNumber/decPacked.c
    decNumber/decQuad.c
    decNumber/decSingle.c)

target_compile_definitions(decNumber
    PUBLIC DECNUMDIGITS=62
    PRIVATE DECPRINT=0 DECLITEND=1 _CRT_SECURE_NO_WARNINGS)

set_property(TARGET decNumber PROPERTY
    MSVC_DEBUG_INFORMATION_FORMAT "$<$<CONFIG:Debug,RelWithDebInfo>:Embedded>")
