set(GEN_EXE
        svshm_attach
        svshm_create
        svshm_mon
        svshm_rm
        svshm_xfr_reader
        svshm_xfr_writer
)

set(LINUX_EXE
        svshm_info
        svshm_lock
        svshm_unlock
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE Threads::Threads)
endforeach ()
