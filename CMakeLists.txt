cmake_minimum_required (VERSION 2.6)
project (SOIL)

add_definitions (-D_CRT_SECURE_NO_WARNINGS)
include_directories (src/SOIL2)
add_library (soil STATIC
    src/SOIL2/etc1_utils.c
    src/SOIL2/etc1_utils.h
    src/SOIL2/image_DXT.c
    src/SOIL2/image_DXT.h
    src/SOIL2/image_helper.c
    src/SOIL2/image_helper.h
    src/SOIL2/pkm_helper.h
    src/SOIL2/pvr_helper.h
    src/SOIL2/SOIL2.c
    src/SOIL2/SOIL2.h
    src/SOIL2/stbi_DDS_c.h
    src/SOIL2/stbi_DDS.h
    src/SOIL2/stbi_ext_c.h
    src/SOIL2/stbi_ext.h
    src/SOIL2/stb_image.h
    src/SOIL2/stb_image_write.h
    src/SOIL2/stbi_pkm_c.h
    src/SOIL2/stbi_pkm.h
    src/SOIL2/stbi_pvr_c.h
    src/SOIL2/stbi_pvr.h)


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
