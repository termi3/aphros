set(CSD "${CMAKE_CURRENT_SOURCE_DIR}")
get_filename_component(p ${CSD} NAME)

set(EXE t.${p})

add_executable(${EXE} main.cpp)

install(TARGETS ${EXE} DESTINATION "${CHPREFIX}/bin")

target_link_libraries(${EXE} distrsolver solver vof vofm tvd overlap curv init_vel)

add_test(NAME adv-loc8 COMMAND runshort tloc 8)
add_test(NAME adv-loc16 COMMAND runshort tloc 16)
add_test(NAME adv-loc32 COMMAND runshort tloc 32 1)
add_test(NAME adv-cub8 COMMAND runshort tcub 8)
add_test(NAME adv-cub16 COMMAND runshort tcub 16)
add_test(NAME adv-cub32 COMMAND runshort tcub 32 1)
add_test(NAME adv-cubm8 COMMAND runshort tcubm 8)
add_test(NAME adv-cubm16 COMMAND runshort tcubm 16)
add_test(NAME adv-cubm32 COMMAND runshort tcubm 32 1)
add_test(NAME adv3d-loc COMMAND run3d tloc3d)
add_test(NAME adv3d-cub COMMAND run3d tcub3d)
add_test(NAME adv3d-cubold COMMAND run3d tcubold3d)

set_tests_properties(
  adv-loc8 adv-loc16 adv-loc32 
  adv-cub8 adv-cub16 adv-cub32 
  adv-cubm8 adv-cubm16 adv-cubm32 
  adv3d-loc adv3d-cub adv3d-cubold
  PROPERTIES RESOURCE_LOCK ${EXE})
