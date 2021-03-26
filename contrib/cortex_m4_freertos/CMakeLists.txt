include("${COMMON_TOOL_ROOT}/cmake/utility/embedded.cmake")

# Header include target
gen_intf_lib(
  TARGET
    segger_sys_view_cortex_m4_freertos_intf
  INTF_INCLUDES
    ./
  EXPORT_DIR
    "${PROJECT_BINARY_DIR}/Aurora/Segger"
)


gen_static_lib_variants(
  TARGET
    segger_sys_view_cortex_m4_freertos
  SOURCES
    sys_view_stubs.cpp
    SEGGER_SYSVIEW_FreeRTOS.c
  PRV_INCLUDES
    ./
  PRV_LIBRARIES
    aurora_intf_inc
    chimera_intf_inc
    freertos_intf_inc_all
    project_inc
  EXPORT_DIR
    "${PROJECT_BINARY_DIR}/Aurora/Segger"
)
