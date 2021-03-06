cmake_minimum_required(VERSION 2.8.8)

#-----------------------------------------------------------------------------
set(MODULE_NAME "NucleusClosing")

#-----------------------------------------------------------------------------
if(NOT Slicer_SOURCE_DIR)
  find_package(Slicer REQUIRED)
  include(${Slicer_USE_FILE})
endif()

#-----------------------------------------------------------------------------
set(MODULE_HOMEPAGE "${_EXT_HOMEPAGE}")
set(MODULE_CATEGORY "${_EXT_CATEGORY}")
set(MODULE_CONTRIBUTORS "${_EXT_CONTRUBUTORS}")
set(MODULE_DESCRIPTION "Produces a outter contour and inner contour for necleus closing" )
set(MODULE_ACKNOWLEDGEMENTS "${_EXT_ACKNOWLEDGEMENTS}")
set(MODULE_LICENSE_SHORT_DESCRIPTION "${MODULE_LICENSE_SHORT_DESCRIPTION}")
set(MODULE_MAJOR_VERSION "${_EXT_MAJOR_VERSION}")
set(MODULE_MINOR_VERSION "${_EXT_MINOR_VERSION}")
set(MODULE_PATCH_VERSION "${_EXT_PATCH_VERSION}")

# Configure XML description
configure_file(
  ${MODULE_NAME}.xml.in
  ${CMAKE_CURRENT_BINARY_DIR}/${MODULE_NAME}.xml
  @ONLY
  )

#-----------------------------------------------------------------------------
set(MODULE_TARGET_LIBRARIES
  ${ITK_LIBRARIES} ${SimpleITK_LIBRARIES}
  )
  
#-----------------------------------------------------------------------------
slicerMacroBuildCLI(
  NAME ${MODULE_NAME}
  TARGET_LIBRARIES ${MODULE_TARGET_LIBRARIES} 
  )

