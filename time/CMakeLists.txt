set(GEN_EXE
        calendar_time
        process_time
        show_time
        strtime
)

set(LINUX_EXE
        # None
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
