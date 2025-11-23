set(GEN_EXE
        # None
)

set(LINUX_EXE
        t_setxattr
        xattr_view
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
