set(GEN_EXE
        # None
)

set(LINUX_EXE
        vdso_gettimeofday
        syscall_gettimeofday
)

set_exe_list()

foreach (exe ${EXE})
    if (${exe} STREQUAL "vdso_gettimeofday")
        add_executable(vdso_gettimeofday gettimeofday.c)
    elseif (${exe} STREQUAL "syscall_gettimeofday")
        add_executable(syscall_gettimeofday gettimeofday.c)
        target_compile_definitions(syscall_gettimeofday PRIVATE USE_SYSCALL)
    endif ()
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
