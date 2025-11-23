set(GEN_EXE
        # None
)

set(LINUX_EXE
        dump_seccomp_filter
        libseccomp_demo
        seccomp_arg64
        seccomp_bench
        seccomp_control_open
        seccomp_deny_open
        seccomp_launch
        seccomp_perf
        # Additional targets not in Makefile's LINUX_EXE but present as rules
        seccomp_unotify_mkdir
        seccomp_unotify_openat
        seccomp_multiarch
)

set_exe_list()

foreach (exe ${EXE})
    if (exe STREQUAL "seccomp_unotify_mkdir" OR exe STREQUAL "seccomp_unotify_openat")
        add_executable(${exe} ${exe}.c seccomp_functions.c)
    else ()
        add_executable(${exe} ${exe}.c)
    endif ()

    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

find_library(LINUX_LIBSECCOMP seccomp)

if (TARGET libseccomp_demo)
    target_link_libraries(libseccomp_demo PRIVATE ${LINUX_LIBSECCOMP})
endif ()
if (TARGET libseccomp_demo)
    target_link_libraries(seccomp_multiarch PRIVATE ${LIBRT})
endif ()
