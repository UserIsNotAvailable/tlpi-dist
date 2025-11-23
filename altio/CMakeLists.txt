set(GEN_EXE
        demo_sigio
        poll_pipes
        select_mq
        self_pipe
        t_select)

set(LINUX_EXE
        epoll_flags_fork
        epoll_input
        multithread_epoll_wait
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

target_link_libraries(multithread_epoll_wait PRIVATE Threads::Threads)