set(GEN_EXE
        t_getpwent
        t_getpwnam_r
)

set(LINUX_EXE
        check_password
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

target_link_libraries(check_password PRIVATE ${LINUX_LIBCRYPT})

