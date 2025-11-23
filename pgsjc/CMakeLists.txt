set(GEN_EXE
        catch_SIGHUP
        disc_SIGHUP
        handling_SIGTSTP
        job_mon
        orphaned_pgrp_SIGHUP
        t_setsid
)

set(LINUX_EXE
        # None
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
