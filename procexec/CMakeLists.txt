set(GEN_EXE
        acct_on
        child_status
        closeonexec
        envargs
        exit_handlers
        footprint
        fork_file_sharing
        fork_sig_sync
        fork_stdio_buf
        fork_whos_on_first
        make_zombie
        multi_SIGCHLD
        multi_wait
        orphan
        t_execl
        t_execle
        t_execve
        t_execlp
        t_fork
        t_system
        t_vfork
        vfork_fd_test
)

set(LINUX_EXE
        demo_clone
        t_clone
        acct_view
        acct_v3_view
        pdeath_signal
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

if (TARGET pdeath_signal)
    target_link_libraries(pdeath_signal PRIVATE Threads::Threads)
endif ()
