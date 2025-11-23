set(GEN_EXE
        # None
)

set(LINUX_EXE
        cap_launcher
        cap_text
        check_password_caps
        demo_file_caps
        show_secbits
        t_cap_get_file
        t_cap_get_pid
        t_cap_set_file
)

# Option to build view_cap_xattr (requires Linux kernel >= 4.14)
option(BUILD_VIEW_CAP_XATTR "Build view_cap_xattr (requires Linux kernel >= 4.14)" OFF)

if (BUILD_VIEW_CAP_XATTR)
    list(APPEND LINUX_EXE view_cap_xattr)
endif ()

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE ${LINUX_LIBCAP})
    target_link_libraries(${exe} PRIVATE ${LIBCRYPT})
endforeach ()

