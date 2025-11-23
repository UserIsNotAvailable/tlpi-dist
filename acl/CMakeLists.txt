set(GEN_EXE
        # None
)

set(LINUX_EXE
        acl_view
        acl_update
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi ${LINUX_LIBACL})
endforeach ()
