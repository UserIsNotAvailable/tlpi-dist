set(GEN_EXE
        t_statvfs
)

set(LINUX_EXE
        t_statfs
        t_mount
        t_umount
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
