set(GEN_EXE
        daemon_SIGHUP
        t_syslog
        test_become_daemon
)

set(LINUX_EXE
        # None
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
