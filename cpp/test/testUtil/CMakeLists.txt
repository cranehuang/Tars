include_directories(${util_SOURCE_DIR}/include)
include_directories(${MYSQL_DIR_INC})

link_libraries(tarsutil)
link_libraries(${MYSQL_DIR_LIB}/libmysqlclient.a)
link_libraries(ssl crypto pthread z dl)
if(NOT APPLE)
	link_libraries(rt)
endif()

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)

FILE(GLOB_RECURSE SRC_LIST "*.cpp")

foreach(FILE ${SRC_LIST})
    get_filename_component(TARGETNAME ${FILE} NAME_WE)
    add_executable(${TARGETNAME} ${FILE})

endforeach(FILE)
