set(GEN_EXE
        # None
)

set(LINUX_EXE
        demo_inotify
        dnotify
        inotify_dtree
        rand_dtree
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
