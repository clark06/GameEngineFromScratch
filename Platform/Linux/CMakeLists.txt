add_executable(MyGameEngineOpenGL XcbApplication.cpp OpenGLApplication.cpp
	${PROJECT_SOURCE_DIR}/External/src/glad/src/glad_glx.c
    )
find_library(XCB_LIBRARY xcb)
find_library(X11_LIBRARY X11)
find_library(X11_XCB_LIBRARY X11-xcb)
find_library(OPENGL_LIBRARY GL)
if(${CMAKE_HOST_SYSTEM_NAME} MATCHES FreeBSD)
set (DL_LIBRARY "")
else(${CMAKE_HOST_SYSTEM_NAME} MATCHES FreeBSD)
find_library(DL_LIBRARY dl)
endif(${CMAKE_HOST_SYSTEM_NAME} MATCHES FreeBSD)
target_link_libraries(MyGameEngineOpenGL OpenGLRHI Common 
        ${OPENGEX_LIBRARY} 
        ${OPENDDL_LIBRARY} 
        ${XG_LIBRARY} 
        ${ZLIB_LIBRARY}
        ${XCB_LIBRARY} 
        ${X11_LIBRARY} 
        ${X11_XCB_LIBRARY} 
        ${OPENGL_LIBRARY} 
        ${DL_LIBRARY})
target_include_directories(MyGameEngineOpenGL PRIVATE "${PROJECT_SOURCE_DIR}/External/src/glad/include")
__add_xg_platform_dependencies(MyGameEngineOpenGL)

