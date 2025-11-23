set(GEN_EXE
        t_uname
)

set(LINUX_EXE
        procfs_pidmax
        procfs_user_exe
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
