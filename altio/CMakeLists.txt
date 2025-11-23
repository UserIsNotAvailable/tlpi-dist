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

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

if (TARGET multithread_epoll_wait)
    target_link_libraries(multithread_epoll_wait PRIVATE Threads::Threads)
endif ()