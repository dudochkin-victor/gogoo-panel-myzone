SET(VERSION_MAJOR 0)
SET(VERSION_MINOR 0)
SET(VERSION_PATCH 0)

INCLUDE_DIRECTORIES(
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_SOURCE_DIR}
    ${CMAKE_CURRENT_BINARY_DIR}
    ${MPL_INCLUDE_DIRS}
    ${MX_INCLUDE_DIRS}
    ${SW_INCLUDE_DIRS}
    ${JANA_INCLUDE_DIRS}
#    ${DBUS_INCLUDE_DIRS}
    ${GCONF_INCLUDE_DIRS}
    )

SET (LIBRARY penge)

SET(LIBRARY_SRCS 
      penge-people-tile.c 
      penge-recent-file-tile.c 
      penge-event-tile.c 
      penge-events-pane.c 
      penge-calendar-pane.c 
      penge-grid-view.c 
      penge-utils.c 
      penge-magic-texture.c 
      penge-view-background.c 
      penge-apps-pane.c 
      penge-app-tile.c 
      penge-task-tile.c 
      penge-tasks-pane.c 
      penge-welcome-tile.c 
      penge-interesting-tile.c 
      penge-block-container.c 
      penge-everything-pane.c 
      penge-clickable-label.c 
      penge-email-pane.c 
      penge-count-tile.c 
      penge-dynamic-box.c
    )

ADD_DEFINITIONS(-DLOCALEDIR="${LOCALEDIR}")
ADD_DEFINITIONS(-DGETTEXT_PACKAGE="${GETTEXT_PACKAGE}")
ADD_DEFINITIONS(-DNBTK_CACHE="${PKG_DATADIR}/nbtk.cache")
ADD_DEFINITIONS(-DTHEMEDIR="${PKG_DATADIR}/theme")

ADD_LIBRARY(${LIBRARY} ${LIBRARY_SRCS})

SET_TARGET_PROPERTIES( ${LIBRARY} PROPERTIES
     SOVERSION 0
     VERSION ${VERSION_MAJOR}.${VERSION_MINOR}.${VERSION_PATCH}
   )


TARGET_LINK_LIBRARIES(${LIBRARY}
    ${MPL_LIBRARIES}
    ${SW_LIBRARIES}
    ${MX_LIBRARIES}
    ${JANA_LIBRARIES}
    ${GCONF_LIBRARIES}
    mailme
    )
