set(GEN_EXE
        clock_times
        cpu_burner
        cpu_multi_burner
        ptmr_null_evp
        ptmr_sigev_signal
        ptmr_sigev_thread
        real_timer
        t_nanosleep
        timed_read
)

set(LINUX_EXE
        cpu_multithread_burner
        demo_timerfd
        t_clock_nanosleep
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE ${LIBRT})
    target_link_libraries(${exe} PRIVATE Threads::Threads)
endforeach ()
