FIND_PACKAGE(ZLIB REQUIRED)

SET(VERSION_MAJOR 0)
SET(VERSION_MINOR 0)
SET(VERSION_PATCH 0)

INCLUDE_DIRECTORIES(
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_SOURCE_DIR}
    ${MPL_INCLUDE_DIRS}
    ${GCONF_INCLUDE_DIRS}
    )


ADD_DEFINITIONS(-DLOCALEDIR=\"$(localedir)\")
ADD_DEFINITIONS(-DMX_CACHE=\"$(pkgdatadir)/mx.cache\")
ADD_DEFINITIONS(-DTHEMEDIR=\"$(pkgdatadir)/netpanel\")
ADD_DEFINITIONS(-DGETTEXT_PACKAGE="meego-panel-web")

SET (PROGRAMS meego-panel-myzone)

SET(PROGRAM_SRCS
	meego-panel-myzone.c
    )

SET(PROGRAM_HEADERS
    )

ADD_EXECUTABLE(${PROGRAMS} ${PROGRAM_SRCS} ${PROGRAM_HEADERS})

   
TARGET_LINK_LIBRARIES(${PROGRAMS}
    penge
    )

INSTALL(TARGETS ${PROGRAMS} RUNTIME DESTINATION ${PKG_LIBEXECDIR})

########### Add .desktop target ###############
#CONFIGURE_FILE(
#  "${CMAKE_CURRENT_SOURCE_DIR}/meego-panel-internet.desktop.in"
#  "${CMAKE_CURRENT_BINARY_DIR}/meego-panel-internet.desktop"
#  IMMEDIATE @ONLY)
#INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/meego-panel-internet.desktop DESTINATION share/mutter-netbook/panels)

########### Add .service target ###############
CONFIGURE_FILE(
  "${CMAKE_CURRENT_SOURCE_DIR}/com.meego.UX.Shell.Panels.myzone.service.in"
  "${CMAKE_CURRENT_BINARY_DIR}/com.meego.UX.Shell.Panels.myzone.service"
  IMMEDIATE @ONLY)
INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/com.meego.UX.Shell.Panels.myzone.service DESTINATION share/dbus-1/services)


