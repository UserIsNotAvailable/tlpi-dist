set(GEN_EXE
        fork_bomb
        fork_bomb_simple
)

set(LINUX_EXE
        alloc_mem
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

if (TARGET alloc_mem)
    target_link_libraries(alloc_mem PRIVATE Threads::Threads)
endif ()
