find_package(SPA)
if (${SPA_FOUND})
	message(STATUS "SPA plugin enabled")
	include_directories(${SPA_INCLUDE_DIRS})
	link_directories(${SPA_LIBRARY_DIRS})
	add_library(zynaddsubfx_spa SHARED
		    ../UI/ConnectionDummy.cpp
		    ../globals.cpp
		    icon.cpp
		    icon.h
		    oscoutput.cpp
		    oscoutput.h)
	target_link_libraries(zynaddsubfx_spa
			      zynaddsubfx_core
			      ${OS_LIBRARIES}
			      ${LIBLO_LIBRARIES}
			      ${SPA_LIBRARIES})
	install(TARGETS zynaddsubfx_spa LIBRARY DESTINATION ${PluginLibDir}/spa/)
endif()

