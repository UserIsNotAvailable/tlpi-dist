set(GEN_EXE
        change_case
        fifo_seqnum_client
        fifo_seqnum_server
        pipe_ls_wc
        pipe_sync
        popen_glob
        simple_pipe
)

set(LINUX_EXE
        # None
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
