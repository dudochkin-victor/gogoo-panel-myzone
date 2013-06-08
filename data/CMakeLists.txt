ADD_SUBDIRECTORY(theme)

########### Add .desktop target ###############
CONFIGURE_FILE(
  "${CMAKE_CURRENT_SOURCE_DIR}/gogoo-panel-myzone.desktop.in"
  "${CMAKE_CURRENT_BINARY_DIR}/gogoo-panel-myzone.desktop"
  IMMEDIATE @ONLY)
INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/gogoo-panel-myzone.desktop DESTINATION ${DATA_DIR}/panels)


