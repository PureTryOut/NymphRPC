set(SRC
	callback_request.cpp
	dispatcher.cpp
	nymph_listener.cpp
	nymph_logger.cpp
	nymph_message.cpp
	nymph_method.cpp
	nymph_server.cpp
	nymph_session.cpp
	nymph_socket_listener.cpp
	nymph_types.cpp
	nymph_utilities.cpp
	remote_client.cpp
	remote_server.cpp
	worker.cpp
)

set(HEADERS
	abstract_request.h
	callback_request.h
	dispatcher.h
	nymph.h
	nymph_listener.h
	nymph_logger.h
	nymph_message.h
	nymph_server.h
	nymph_session.h
	nymph_socket_listener.h
	nymph_types.h
	nymph_utilities.h
	remote_client.h
	remote_server.h
	worker.h
)

add_library(
	nymphrpc SHARED
	${SRC}
)

target_link_libraries(
	nymphrpc
	Poco::Foundation
	Poco::JSON
	Poco::Net
)

target_include_directories(
	nymphrpc
	PUBLIC
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
	$<INSTALL_INTERFACE:include/libnymphrpc>
)

set_target_properties(
	nymphrpc PROPERTIES
	SOVERSION ${PROJECT_VERSION_MAJOR}
	VERSION ${PROJECT_VERSION}
)

install(
	TARGETS nymphrpc LIBRARY
	DESTINATION ${CMAKE_INSTALL_LIBDIR}
)

install(
	FILES ${HEADERS}
	DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/nymph
)
