set(GEN_EXE
        mix23_linebuff
        mix23io
        write_bytes
        # Variants of write_bytes handled below
)

set(LINUX_EXE
        direct_read
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()

# Special targets for write_bytes variants

# write_bytes_fdatasync : write_bytes.c -DUSE_FDATASYNC
add_executable(write_bytes_fdatasync write_bytes.c)
target_compile_definitions(write_bytes_fdatasync PRIVATE USE_FDATASYNC)
target_link_libraries(write_bytes_fdatasync PRIVATE tlpi)

# write_bytes_fsync : write_bytes.c -DUSE_FSYNC
add_executable(write_bytes_fsync write_bytes.c)
target_compile_definitions(write_bytes_fsync PRIVATE USE_FSYNC)
target_link_libraries(write_bytes_fsync PRIVATE tlpi)

# write_bytes_o_sync : write_bytes.c -DUSE_O_SYNC
add_executable(write_bytes_o_sync write_bytes.c)
target_compile_definitions(write_bytes_o_sync PRIVATE USE_O_SYNC)
target_link_libraries(write_bytes_o_sync PRIVATE tlpi)
