set(GEN_EXE
        # None
)

set(LINUX_EXE
        acl_view
        acl_update
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi ${LINUX_LIBACL})
endforeach ()
