set(GEN_EXE
        svmsg_chqbytes
        svmsg_file_client
        svmsg_file_server
        svmsg_create
        svmsg_receive
        svmsg_rm
        svmsg_send
)

set(LINUX_EXE
        svmsg_info
        svmsg_ls
)

set_exe_list()

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
