project(ItkVtkGlue)
include(CPack)
cmake_minimum_required(VERSION 2.8)

option(BUILD_WRAPPERS "Wrap library" OFF)
option(INSTALL_DEVEL_FILES "Install C++ headers" ON)

find_package(ITK REQUIRED)
find_package(VTK REQUIRED)

include_directories(${VTK_INCLUDE_DIRS} ${ITK_INCLUDE_DIRS} ${ItkVtkGlue_SOURCE_DIR}/src)
link_directories(${VTK_LIBRARY_DIRS} ${ITK_LIBRARY_DIRS})

if(BUILD_WRAPPERS)
   subdirs(Wrapping)
endif()

# install devel files
if(INSTALL_DEVEL_FILES)
  foreach(f itkImageToVTKImageFilter.h itkImageToVTKImageFilter.txx itkVTKImageToImageFilter.h itkVTKImageToImageFilter.txx)
    install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/src/${f} DESTINATION include/InsightToolkit/BasicFilters)
  endforeach()
endif()

enable_testing()
