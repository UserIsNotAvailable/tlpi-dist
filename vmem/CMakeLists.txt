set(GEN_EXE
        memlock
        madvise_dontneed
)

set(LINUX_EXE
        t_mprotect
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
