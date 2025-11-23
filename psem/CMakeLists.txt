set(GEN_EXE
        psem_create
        psem_getvalue
        psem_post
        psem_timedwait
        psem_trywait
        psem_unlink
        psem_wait
        thread_incr_psem
)

set(LINUX_EXE
        # None
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE Threads::Threads)
endforeach ()

if (TARGET psem_timedwait)
    target_link_libraries(psem_timedwait PRIVATE ${LIBRT})
endif ()
