file (GLOB HEADERS "*.h")
file (GLOB SOURCES "[^_]*.cpp")

set(BIN texrecon)

add_executable(${BIN} ${SOURCES})
set_property(TARGET ${BIN} PROPERTY INTERPROCEDURAL_OPTIMIZATION True)
add_dependencies(${BIN} ext_mve)
target_link_libraries(${BIN} tex ${TBB_LIBRARIES} OpenMP::OpenMP_CXX -lmve -lmve_util)
install(TARGETS ${BIN} RUNTIME DESTINATION bin)
