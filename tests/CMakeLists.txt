include_directories (${CMAKE_SOURCE_DIR}/CheMPS2/include/ ${HDF5_INCLUDE_DIRS})

link_directories (${CMAKE_BINARY_DIR}/CheMPS2)

file (MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/tests/tests)

set (TESTLIST "test1" "test2" "test3" "test4" "test5" "test6" "test7" "test8" "test9")

foreach (ITEM ${TESTLIST})
    configure_file (${CMAKE_SOURCE_DIR}/tests/${ITEM}.cpp.in ${CMAKE_BINARY_DIR}/tests/tests/${ITEM}.cpp)
    add_executable (${ITEM} ${CMAKE_BINARY_DIR}/tests/tests/${ITEM}.cpp)
    target_link_libraries (${ITEM} chemps2)
    add_test(${ITEM} ${ITEM})
endforeach (ITEM)

