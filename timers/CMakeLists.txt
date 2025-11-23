set(GEN_EXE
        clock_times
        cpu_burner
        cpu_multi_burner
        cpu_multithread_burner
        ptmr_null_evp
        ptmr_sigev_signal
        ptmr_sigev_thread
        real_timer
        t_nanosleep
        timed_read
)

set(LINUX_EXE
        demo_timerfd
        t_clock_nanosleep
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE ${LINUX_LIBRT})
    target_link_libraries(${exe} PRIVATE Threads::Threads)
endforeach ()
