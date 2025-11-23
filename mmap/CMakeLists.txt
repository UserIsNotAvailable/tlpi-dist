set(GEN_EXE
        anon_mmap
        mmcat
        mmcopy
        t_mmap
)

set(LINUX_EXE
        t_remap_file_pages
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
