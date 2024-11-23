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

target_compile_definitions(decNumber PRIVATE
    DECNUMDIGITS=62
    DECPRINT=0
    DECLITEND=1
    _CRT_SECURE_NO_WARNINGS)

install(DIRECTORY
    ${CMAKE_SOURCE_DIR}/decNumber/
	
	DESTINATION include/${PROJECT_NAME}
	FILES_MATCHING
	PATTERN "*.h"
)

install(TARGETS ${PROJECT_NAME} EXPORT ${PROJECT_NAME}_targets)

# Generate and install *-targets.cmake 
install(EXPORT ${PROJECT_NAME}_targets
  FILE ${PROJECT_NAME}-targets.cmake
  DESTINATION share/${PROJECT_NAME}
)

# Generate the config file in the current binary dir (this ensures it's not placed directly in source)
file(WRITE "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}-config.cmake"
  "include(\"\${CMAKE_CURRENT_LIST_DIR}/${PROJECT_NAME}-targets.cmake\")\n"
)

# Install the generated config file
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}-config.cmake"
  DESTINATION share/${PROJECT_NAME}
)
