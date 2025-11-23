set(GEN_EXE
        rusage
        rusage_wait
)

set(LINUX_EXE
        rlimit_nproc
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
