set(GEN_EXE
        i6d_ucase_sv
        i6d_ucase_cl
        id_echo_cl
        id_echo_sv
        is_echo_cl
        is_echo_sv
        is_echo_inetd_sv
        is_echo_v2_sv
        is_seqnum_sv
        is_seqnum_cl
        is_seqnum_v2_sv
        is_seqnum_v2_cl
        socknames
        t_gethostbyname
        t_getservbyname
        ud_ucase_sv
        ud_ucase_cl
        us_xfr_cl
        us_xfr_sv
        us_xfr_v2_cl
        us_xfr_v2_sv
)

set(LINUX_EXE
        list_host_addresses
        scm_cred_recv
        scm_cred_send
        scm_multi_recv
        scm_multi_send
        scm_rights_recv
        scm_rights_send
        us_abstract_bind
)

set(EXE ${GEN_EXE} ${LINUX_EXE})

foreach (exe ${EXE})
    add_executable(${exe} ${exe}.c)
    target_link_libraries(${exe} PRIVATE tlpi)
endforeach ()
