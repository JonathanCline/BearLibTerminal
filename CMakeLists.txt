



set(_IncludeRoot "${CMAKE_CURRENT_LIST_DIR}/Include/C/")

add_library(BearLibTerminal SHARED IMPORTED GLOBAL)

set(_LinkRoot )

if (DEFINED TARGET_SYSTEM)
	if(TARGET_SYSTEM STREQUAL "Win64")
		set(_LinkRoot "${CMAKE_CURRENT_LIST_DIR}/Windows64")
	elseif(TARGET_SYSTEM STREQUAL "Win32")
		set(_LinkRoot "${CMAKE_CURRENT_LIST_DIR}/Windows32")
	endif()
else()
	set(_LinkRoot "${CMAKE_CURRENT_LIST_DIR}/Windows64")
endif()

if (WIN32)
	set_target_properties(BearLibTerminal PROPERTIES IMPORTED_IMPLIB "${_LinkRoot}/BearLibTerminal.lib")
	set_target_properties(BearLibTerminal PROPERTIES IMPORTED_LOCATION "${_LinkRoot}/BearLibTerminal.dll")
	target_include_directories(BearLibTerminal INTERFACE "${_IncludeRoot}")
else()
	message(FATAL_ERROR "Fix me")
endif()
