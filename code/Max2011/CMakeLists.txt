
IF ( MSVC90 )
			
	#######################################################
	# P L U G I N   F O R   3 D S M A X   2 0 1 1         #
	#######################################################
	
	INCLUDE_DIRECTORIES ( ${MAXSDK_2011_HEADERS_DIR} )
	LINK_DIRECTORIES ( ${MAXSDK_2011_LIBRARY_DIR} )
	
	ADD_LIBRARY ( ${PROJECT_NAME_MAX_2011} SHARED ${SOURCE_FILES} ${HEADER_FILES} ${RESOURCE_FILES} )
	TARGET_LINK_LIBRARIES( ${PROJECT_NAME_MAX_2011} ${MAX_LIBS} )

	SET_TARGET_PROPERTIES( ${PROJECT_NAME_MAX_2011} PROPERTIES OUTPUT_NAME "Max2011/TexLay" )
	SET_TARGET_PROPERTIES( ${PROJECT_NAME_MAX_2011} PROPERTIES SUFFIX ".dlm" )
	SET_TARGET_PROPERTIES( ${PROJECT_NAME_MAX_2011} PROPERTIES CLEAN_DIRECT_OUTPUT 1 )	

	SET ( LOCAL_WARNING_FLAGS /W3 )
	SET ( LOCAL_RTTI_FLAGS /GR )
	
	ADD_CUSTOM_COMMAND( TARGET ${PROJECT_NAME_MAX_2011} POST_BUILD COMMAND copy .\\$(ConfigurationName)\\Max2011\\TexLay.dlm "${PROGRAM_FILES}\\Autodesk\\3ds Max 2011\\plugins" )
	
ENDIF ( MSVC90 )

