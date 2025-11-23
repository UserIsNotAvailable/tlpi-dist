set(GEN_EXE
        alloc_mem
        fork_bomb
        fork_bomb_simple
)

set(LINUX_EXE
        # None
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

target_link_libraries(alloc_mem PRIVATE Threads::Threads)
