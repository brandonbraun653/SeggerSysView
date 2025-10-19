include(CTEmbedded)


add_subdirectory(contrib/cortex_m4_freertos)

# Header include target
gen_intf_lib(
  TARGET
    segger_sys_view_intf
  INTF_INCLUDES
    ./Config
    ./SEGGER
    ./SEGGER/Syscalls
  INTF_LIBRARIES
    project_intf_inc
  EXPORT_DIR
    "${PROJECT_BINARY_DIR}/Aurora/Segger"
)

# Library target
gen_static_lib_variants(
  TARGET
    segger_sys_view
  SOURCES
    SEGGER/SEGGER_RTT_ASM_ARMv7M.S
    SEGGER/SEGGER_RTT_printf.c
    SEGGER/SEGGER_RTT.c
    SEGGER/SEGGER_SYSVIEW.c
  PRV_LIBRARIES
    segger_sys_view_intf
  EXPORT_DIR
    "${PROJECT_BINARY_DIR}/Aurora/Segger"
)

gen_static_lib_variants(
  TARGET
    segger_sys_view_printf
  SOURCES
    SEGGER/Syscalls/SEGGER_RTT_Syscalls_GCC.c
  PRV_LIBRARIES
    segger_sys_view_intf
  EXPORT_DIR
    "${PROJECT_BINARY_DIR}/Aurora/Segger"
)