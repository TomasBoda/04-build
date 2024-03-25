
set(SOURCES
    btree_int.c conds.c config.c data.c db_engine.c db_main.c error.c index.c memory.c parser_commands.c parser_conds.c query.c result.c sql_parser.c strutil.c tabconf.c tabdef.c textfileio.c
)

set(HEADERS
    btree_int.h conds.h config.h data.h db_engine.h db_main.h defs.h error.h index.h linklist.h memory.h parser_commands.h parser_conds.h query.h result.h sql_parser.h strutil.h tabconf.h tabdef.h textfileio.h
)

add_library(mydb STATIC ${SOURCES})

target_include_directories(mydb PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

add_executable(testclient testclient.c client_comm.c)
add_executable(testserver testserver.c server_comm.c)
add_executable(testadmin testadmin.c)

target_link_libraries(testclient mydb readline)
target_link_libraries(testserver mydb)
target_link_libraries(testadmin mydb readline)