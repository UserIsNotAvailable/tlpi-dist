set(GEN_EXE
        atomic_append
        bad_exclusive_open
        copy
        multi_descriptors
        seek_io
        t_readv
        t_truncate
)

set(LINUX_EXE
        large_file
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
