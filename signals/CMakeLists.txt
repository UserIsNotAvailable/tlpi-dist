set(GEN_EXE
        catch_rtsigs
        demo_SIGFPE
        ignore_pending_sig
        intquit
        nonreentrant
        ouch
        sig_receiver
        sig_sender
        sig_speed_sigsuspend
        sigmask_longjmp
        sigmask_siglongjmp
        t_kill
        t_sigaltstack
        t_sigsuspend
        t_sigqueue
        t_sigwaitinfo
)

set(LINUX_EXE
        signalfd_sigval
)

set_exe_list()

foreach (exe ${EXE})
    if (exe STREQUAL "sigmask_siglongjmp")
        add_executable(${exe} sigmask_longjmp.c)
    else ()
        add_executable(${exe} ${exe}.c)
    endif ()

    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

foreach (exe ouch intquit sig_receiver)
    target_compile_definitions(${exe} PRIVATE _BSD_SOURCE)
endforeach ()

target_link_libraries(nonreentrant PRIVATE ${LIBCRYPT})
target_compile_definitions(sigmask_siglongjmp PRIVATE USE_SIGSETJMP)
