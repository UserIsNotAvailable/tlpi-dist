cmake_minimum_required(VERSION 3.10)

project(TLPI VERSION 1.0 LANGUAGES C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_compile_options(
        -D_XOPEN_SOURCE=600
        -D_DEFAULT_SOURCE
        -g
        -pedantic
        -Wall
        -W
        -Wmissing-prototypes
        -Wno-sign-compare
        -Wno-unused-parameter
)

if (CMAKE_C_COMPILER_ID MATCHES "GNU")
    add_compile_options(-Wimplicit-fallthrough)
endif ()

if (CMAKE_C_COMPILER_ID MATCHES "Clang")
    add_compile_options(
            -Wno-uninitialized
            -Wno-infinite-recursion
            -Wno-format-pedantic
    )
endif ()

find_library(LINUX_LIBRT rt)
find_library(LINUX_LIBDL dl)
find_library(LINUX_LIBACL acl)
find_library(LINUX_LIBCRYPT crypt)
find_library(LINUX_LIBCAP cap)

set(CMAKE_THREAD_PREFER_PTHREAD TRUE)
set(THREADS_PREFER_PTHREAD_FLAG TRUE)
find_package(Threads REQUIRED)

set(DIRS
        lib
        acl altio
        cap cgroups
        daemons dirs_links
        filebuff fileio filelock files filesys
        getopt
        inotify
        loginacct
        memalloc
        mmap
        pgsjc pipes pmsg
        proc proccred procexec procpri procres
        progconc
        psem pshm pty
        shlibs
        signals sockets
        svipc svmsg svsem svshm
        sysinfo
        syslim
        threads time timers tty
        users_groups
        vdso
        vmem
        xattr
)

# The "namespaces" and "seccomp" directories are deliberately excluded from
# the above list because much of the code in those directories requires a
# relatively recent kernel and userspace to build. Nevertheless, each of
# those directories contains a Makefile.
option(BUILD_NAMESPACES "Build namespaces examples (requires recent kernel)" OFF)
option(BUILD_SECCOMP "Build seccomp examples (requires recent kernel)" ON)

if (BUILD_NAMESPACES)
    list(APPEND DIRS namespaces)
endif ()

if (BUILD_SECCOMP)
    list(APPEND DIRS seccomp)
endif ()

set(BUILD_DIRS ${DIRS})

foreach (dir ${BUILD_DIRS})
    add_subdirectory(${dir})
endforeach ()
