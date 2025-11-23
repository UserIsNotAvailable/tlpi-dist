set(GEN_EXE
        t_getpwent
        t_getpwnam_r
)

set(LINUX_EXE
        check_password
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

if (TARGET check_password)
    target_link_libraries(check_password PRIVATE ${LIBCRYPT})
endif ()
