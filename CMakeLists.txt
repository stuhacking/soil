project (SOIL)
cmake_minimum_required (VERSION 2.6)

add_definitions (-D_CRT_SECURE_NO_WARNINGS)
include_directories (include src)
add_library (${PROJECT_NAME} STATIC
        src/SOIL.c
        src/etc1_utils.c
        src/image_DXT.c
        src/image_helper.c
        src/stbi_DDS_c.h
        src/stbi_ext_c.h
        src/stbi_pkm_c.h
        src/stbi_pvr_c.h)

# doc
find_package (Doxygen)

if (DOXYGEN_FOUND)

  configure_file (
    ${CMAKE_CURRENT_SOURCE_DIR}/Doxyfile.in
    ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile @ONLY)

  add_custom_target (soil_doc
    ${DOXYGEN_EXECUTABLE} ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile
    WORKING DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Generating API documentation with Doxygen" VERBATIM)

endif (DOXYGEN_FOUND)
