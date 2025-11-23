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

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE Threads::Threads)
endforeach ()

target_link_libraries(psem_timedwait PRIVATE ${LINUX_LIBRT})

