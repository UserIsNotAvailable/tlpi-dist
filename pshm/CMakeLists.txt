set(GEN_EXE
        pshm_create
        pshm_read
        pshm_unlink
        pshm_write
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
