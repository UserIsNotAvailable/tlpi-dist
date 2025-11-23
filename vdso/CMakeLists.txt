set(GEN_EXE
        # None
)

set(LINUX_EXE
        vdso_gettimeofday
        syscall_gettimeofday
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

add_executable(vdso_gettimeofday gettimeofday.c)
target_link_libraries(vdso_gettimeofday PRIVATE tlpi)

add_executable(syscall_gettimeofday gettimeofday.c)
target_compile_definitions(syscall_gettimeofday PRIVATE USE_SYSCALL)
target_link_libraries(syscall_gettimeofday PRIVATE tlpi)
