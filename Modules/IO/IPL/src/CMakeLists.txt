set(ITKIOIPL_SRC
itkIPLCommonImageIO.cxx
itkIPLFileNameList.cxx
)

add_library(ITKIOIPL ${ITKIOIPL_SRC})
target_link_libraries(ITKIOIPL  ${ITKIOImageBase_LIBRARIES})
itk_module_target(ITKIOIPL)
