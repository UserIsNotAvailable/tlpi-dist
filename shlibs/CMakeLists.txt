set(GEN_EXE
        dynload
)

set(LINUX_EXE
        # None
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

if (TARGET dynload)
    target_link_libraries(dynload PRIVATE ${LINUX_LIBDL})
endif ()
