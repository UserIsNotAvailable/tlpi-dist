set(GEN_EXE
        bad_longjmp
        display_env
        longjmp
        necho
        setjmp_vars
        #    setjmp_vars_opt
        t_getenv
)

set(LINUX_EXE
        modify_env
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
