set(GEN_EXE
        sched_set
        sched_view
        t_setpriority
)

set(LINUX_EXE
        demo_sched_fifo
        t_sched_setaffinity
        t_sched_getaffinity
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
