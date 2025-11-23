set(GEN_EXE
        detached_attrib
        one_time_init
        prod_condvar
        prod_no_condvar
        pthread_barrier_demo
        simple_thread
        thread_cancel
        thread_cleanup
        thread_incr
        thread_incr_mutex
        thread_incr_rwlock
        thread_incr_spinlock
        thread_lock_speed
        thread_multijoin
        # fixme
        #        strerror_test
        #        strerror_test_tsd
        #        strerror_test_tls
)

set(LINUX_EXE
        # None
)

set_exe_list()

foreach (exe ${EXE})
    # fixme
    #    if (${exe} STREQUAL "strerror_test")
    #        add_executable(${exe} strerror_test.c strerror.c)
    #    elseif (${exe} STREQUAL "strerror_test_tsd")
    #        add_executable(${exe} strerror_test.c strerror_tsd.c)
    #    elseif (${exe} STREQUAL "strerror_test_tls")
    #        add_executable(${exe} strerror_test.c strerror_tls.c)
    #    else ()
    add_executable(${exe} ${exe}.c)
    #    endif ()

    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE Threads::Threads)
endforeach ()
