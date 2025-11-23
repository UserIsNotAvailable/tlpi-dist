file(GLOB LIB_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.c")

add_custom_command(
        OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/ename.c.inc
        COMMAND sh ${CMAKE_CURRENT_SOURCE_DIR}/Build_ename.sh > ${CMAKE_CURRENT_BINARY_DIR}/ename.c.inc
        COMMAND ${CMAKE_COMMAND} -E echo "ename.c.inc built"
        WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
        DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/Build_ename.sh
        COMMENT "Building ename.c.inc"
        VERBATIM
)

add_custom_target(generate_ename
        DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/ename.c.inc
)

add_library(tlpi STATIC ${LIB_SOURCES})

add_dependencies(tlpi generate_ename)

target_include_directories(tlpi
        PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
        ${CMAKE_CURRENT_BINARY_DIR}
)
