set(GEN_EXE
        bad_symlink
        file_type_stats
        list_files
        list_files_readdir_r
        nftw_dir_tree
        t_dirbasename
        t_unlink
        view_symlink
)

set(LINUX_EXE
        # None
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
