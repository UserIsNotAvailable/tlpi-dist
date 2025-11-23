set(GEN_EXE
        acct_on
        acct_view
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
        pdeath_signal
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
        acct_v3_view
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

target_link_libraries(pdeath_signal PRIVATE Threads::Threads)
