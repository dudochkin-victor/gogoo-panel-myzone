SET(VERSION_MAJOR 0)
SET(VERSION_MINOR 0)
SET(VERSION_PATCH 0)

INCLUDE_DIRECTORIES(
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_BINARY_DIR}
    ${MX_INCLUDE_DIRS}
    ${DBUS_INCLUDE_DIRS}
    ${GCONF_INCLUDE_DIRS}
    )

SET (LIBRARY myzone)

SET(LIBRARY_SRCS 
	myzone-cc-panel.c 
	myzone-cc-panel.h 
	gconf-bridge.c 
	gconf-bridge.h
    )

#ADD_DEFINITIONS(-DLOCALEDIR="${LOCALEDIR}")
#ADD_DEFINITIONS(-DMX_CACHE="${DATADIR}/mx.cache")
#ADD_DEFINITIONS(-DGETTEXT_PACKAGE="${GETTEXT_PACKAGE}")
#ADD_DEFINITIONS(-DLIBEXECDIR="${PKG_LIBEXECDIR}")
#ADD_DEFINITIONS(-DPKG_DATA_DIR="${PKG_DATADIR}")

ADD_DEFINITIONS(-DEGG_CONSOLE="MPD_CONSOLE")
ADD_DEFINITIONS(-DEGG_LOGGING="MPD_LOGGING")
ADD_DEFINITIONS(-DEGG_LOG_FILE="/tmp/meego-panel-devices.log")
ADD_DEFINITIONS(-DEGG_VERBOSE="MPD_VERBOSE")


ADD_LIBRARY(${LIBRARY} ${LIBRARY_SRCS})

SET_TARGET_PROPERTIES( ${LIBRARY} PROPERTIES
     SOVERSION 0
     VERSION ${VERSION_MAJOR}.${VERSION_MINOR}.${VERSION_PATCH}
   )


TARGET_LINK_LIBRARIES(${LIBRARY}
    ${MX_LIBRARIES}
    )
