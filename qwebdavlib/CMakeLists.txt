find_package(Qt6 REQUIRED COMPONENTS Core Network Xml)
include_directories(${Qt6Network_INCLUDE_DIRS})
include_directories(${Qt6Xml_INCLUDE_DIRS})

add_definitions(-DQWEBDAV_LIBRARY)

list(APPEND SOURCES
    qnaturalsort.cpp
    qwebdav.cpp
    qwebdavitem.cpp
    qwebdavdirparser.cpp
)

list(APPEND HEADERS
    qnaturalsort.h
    qwebdav.h
    qwebdavitem.h
    qwebdavdirparser.h
    qwebdav_global.h
)

add_library(qwebdavlib ${SOURCES})

set_target_properties(qwebdavlib PROPERTIES
    SOVERSION 1.0.0
)

set_property(TARGET qwebdavlib PROPERTY AUTOMOC ON)

target_link_libraries(qwebdavlib PRIVATE
    Qt::Core
    Qt::Network
    Qt::Xml
)

