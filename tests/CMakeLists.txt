
find_program(BATS_EXE bats)
if(EXISTS ${BATS_EXE})
    add_test(NAME duplo-tests
             COMMAND ${BATS_EXE} --recursive ${CMAKE_CURRENT_BINARY_DIR}
             WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} )
    set_tests_properties( duplo-tests PROPERTIES
                          ENVIRONMENT DUPLO=$<TARGET_FILE:duplo>)
endif()
