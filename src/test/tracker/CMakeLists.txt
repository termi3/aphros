set(CSD "${CMAKE_CURRENT_SOURCE_DIR}")
get_filename_component(p ${CSD} NAME)

set(EXE t.${p})

add_executable(${EXE} main.cpp)

target_link_libraries(${EXE} suspender timer)

#add_test(NAME ${p} COMMAND /bin/bash -c "diff ref <(./${EXE})")
add_test(NAME ${p} COMMAND ${EXE})

