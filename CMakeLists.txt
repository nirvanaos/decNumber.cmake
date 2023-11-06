cmake_minimum_required(VERSION 3.15)
project(decNumber C)

add_library(decNumber
    decNumber/decContext.c
    decNumber/decDouble.c
    decNumber/decNumber.c
    decNumber/decPacked.c
    decNumber/decQuad.c
    decNumber/decSingle.c)

target_compile_definitions(decNumber
    PUBLIC DECNUMDIGITS=62
    PRIVATE DECPRINT=0 DDECLITEND=1 _CRT_SECURE_NO_WARNINGS)
    
target_include_directories(decNumber PUBLIC decNumber)

#install(TARGETS decNumber)
