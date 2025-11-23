set(GEN_EXE
        svsem_create
        svsem_demo
        svsem_mon
        svsem_op
        svsem_rm
        svsem_setall
)

set(LINUX_EXE
        svsem_info
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
