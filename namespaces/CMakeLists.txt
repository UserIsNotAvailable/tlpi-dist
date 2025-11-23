set(GEN_EXE
        make_orphans
        orphan
)

set(LINUX_EXE
        cred_launcher
        demo_userns
        demo_uts_namespaces
        hostname
        multi_pidns
        ns_capable
        ns_child_exec
        ns_exec
        ns_run
        pidns_init_sleep
        show_creds
        simple_init
        t_setns_userns
        unshare
        userns_child_exec
        userns_setns_test
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
    target_link_libraries(${exe} PRIVATE ${LINUX_LIBCAP})
endforeach ()
