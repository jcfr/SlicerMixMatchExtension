cmake_minimum_required(VERSION 2.8.9)

project(SlicerMixMatchExtension)

#-----------------------------------------------------------------------------
# Extension meta-information
set(EXTENSION_HOMEPAGE "http://github.com/jcfr/SlicerMixMatchExtension")
set(EXTENSION_CATEGORY "Examples")
set(EXTENSION_CONTRIBUTORS "Jean-Christophe Fillion-Robin (Kitware)")
set(EXTENSION_DESCRIPTION "This extension illustrates how to reuse module components.")
set(EXTENSION_ICONURL "https://raw.github.com/jcfr/SlicerMixMatchExtension/master/SlicerMixMatchExtension.png")
set(EXTENSION_SCREENSHOTURLS "")

#-----------------------------------------------------------------------------
# Extension dependencies
find_package(Slicer REQUIRED)
include(${Slicer_USE_FILE})

#-----------------------------------------------------------------------------
# Extension modules
add_subdirectory(ScriptedMixMatch)
## NEXT_MODULE

#-----------------------------------------------------------------------------
include(${Slicer_EXTENSION_CPACK})
