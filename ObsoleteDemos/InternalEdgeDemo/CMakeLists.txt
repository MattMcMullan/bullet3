# This is basically the overall name of the project in Visual Studio this is the name of the Solution File


# For every executable you have with a main method you should have an add_executable line below.
# For every add executable line you should list every .cpp and .h file you have associated with that executable.  



# You shouldn't have to modify anything below this line 
########################################################

IF (USE_GLUT)
	INCLUDE_DIRECTORIES(
	${BULLET_PHYSICS_SOURCE_DIR}/src 
	../OpenGL 
	)

	LINK_LIBRARIES(
	OpenGLSupport BulletDynamics  BulletCollision LinearMath    ${GLUT_glut_LIBRARY} ${OPENGL_gl_LIBRARY} ${OPENGL_glu_LIBRARY}
	)

	ADD_EXECUTABLE(AppInternalEdgeDemo
        	InternalEdgeDemo.cpp
        	InternalEdgeDemo.h
        	main.cpp
	)
ELSE (USE_GLUT)
	
	INCLUDE_DIRECTORIES(
	${BULLET_PHYSICS_SOURCE_DIR}/src 
	../OpenGL 
	)

	LINK_LIBRARIES(
	OpenGLSupport BulletDynamics  BulletCollision LinearMath   ${OPENGL_gl_LIBRARY} ${OPENGL_glu_LIBRARY}
	)

	ADD_EXECUTABLE(AppInternalEdgeDemo
			WIN32
			../OpenGL/Win32AppMain.cpp
        	InternalEdgeDemo.cpp
        	InternalEdgeDemo.h
        	Win32InternalEdgeDemo.cpp
	)

ENDIF (USE_GLUT)



IF (INTERNAL_ADD_POSTFIX_EXECUTABLE_NAMES)
			SET_TARGET_PROPERTIES(AppInternalEdgeDemo PROPERTIES  DEBUG_POSTFIX "_Debug")
			SET_TARGET_PROPERTIES(AppInternalEdgeDemo PROPERTIES  MINSIZEREL_POSTFIX "_MinsizeRel")
			SET_TARGET_PROPERTIES(AppInternalEdgeDemo PROPERTIES  RELWITHDEBINFO_POSTFIX "_RelWithDebugInfo")
ENDIF(INTERNAL_ADD_POSTFIX_EXECUTABLE_NAMES)