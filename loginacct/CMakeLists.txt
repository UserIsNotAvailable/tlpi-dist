set(GEN_EXE
        # None
)

set(LINUX_EXE
        dump_utmpx
        utmpx_login
        view_lastlog
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
