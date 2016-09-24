add_executable(main main.cpp)
target_link_libraries(main foo)
install(TARGETS main RUNTIME DESTINATION ${CMAKE_SOURCE_DIR}/bin)
