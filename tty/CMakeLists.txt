set(GEN_EXE
        demo_SIGWINCH
        new_intr
        no_echo
        test_tty_functions
)

set(LINUX_EXE
        # None
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
