set(GEN_EXE
        t_chown
        t_stat
        t_umask
        t_utime
        t_utimes
)

set(LINUX_EXE
        chiflag
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
