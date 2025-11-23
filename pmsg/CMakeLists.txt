set(GEN_EXE
        mq_notify_sig
        mq_notify_sigwaitinfo
        mq_notify_thread
        mq_notify_via_signal
        mq_notify_via_thread
        pmsg_create
        pmsg_getattr
        pmsg_receive
        pmsg_send
        pmsg_unlink
)

set(LINUX_EXE
        # None
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE ${LINUX_LIBRT})
endforeach ()

target_link_libraries(mq_notify_thread PRIVATE Threads::Threads)
target_link_libraries(mq_notify_via_thread PRIVATE Threads::Threads)
