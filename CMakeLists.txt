include("${COMMON_TOOL_ROOT}/cmake/utility/embedded.cmake")


# Header include target
gen_intf_lib(
  TARGET
    segger_sys_view_intf
  INTF_INCLUDES
    ./Config
    ./SEGGER
    ./SEGGER/Syscalls
  EXPORT_DIR
    "${PROJECT_BINARY_DIR}/Segger"
)

# Library target
gen_static_lib_variants(
  TARGET
    segger_sys_view
  SOURCES
    SEGGER/Syscalls/SEGGER_RTT_Syscalls_GCC.c
    SEGGER/SEGGER_RTT_ASM_ARMv7M.S
    SEGGER/SEGGER_RTT_printf.c
    SEGGER/SEGGER_RTT.c
    SEGGER/SEGGER_SYSVIEW.c
  PRV_LIBRARIES
    segger_sys_view_intf
  EXPORT_DIR
    "${PROJECT_BINARY_DIR}/Segger"
)