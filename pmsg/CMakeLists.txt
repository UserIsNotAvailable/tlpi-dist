set(GEN_EXE
        mq_notify_sig
        mq_notify_siginfo
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

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE ${LIBRT})
endforeach ()

if (TARGET mq_notify_thread)
    target_link_libraries(mq_notify_thread PRIVATE Threads::Threads)
endif ()
if (TARGET mq_notify_via_thread)
    target_link_libraries(mq_notify_via_thread PRIVATE Threads::Threads)
endif ()
