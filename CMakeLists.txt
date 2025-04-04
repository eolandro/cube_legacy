cmake_minimum_required(VERSION  3.18)

project(cube)
##################
# include
#include(ExternalProject)
##################
# find
find_package(SDL REQUIRED)
find_package(SDL_mixer REQUIRED)
find_package(SDL_image REQUIRED)
find_package(X11 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
find_package(ZLIB REQUIRED)
##################
# enet
add_subdirectory(enet)


### Source files
set(SOURCE_FILES_PREFIX src)
set(SOURCE_CLIENT
	${SOURCE_FILES_PREFIX}/client.cpp
	${SOURCE_FILES_PREFIX}/clientextras.cpp
	${SOURCE_FILES_PREFIX}/clientgame.cpp
	${SOURCE_FILES_PREFIX}/clients2c.cpp
	${SOURCE_FILES_PREFIX}/command.cpp
	${SOURCE_FILES_PREFIX}/console.cpp
	${SOURCE_FILES_PREFIX}/editing.cpp
	${SOURCE_FILES_PREFIX}/entities.cpp
	${SOURCE_FILES_PREFIX}/main.cpp
	${SOURCE_FILES_PREFIX}/menus.cpp
	${SOURCE_FILES_PREFIX}/monster.cpp
	${SOURCE_FILES_PREFIX}/physics.cpp
	${SOURCE_FILES_PREFIX}/rendercubes.cpp
	${SOURCE_FILES_PREFIX}/renderextras.cpp
	${SOURCE_FILES_PREFIX}/rendergl.cpp
	${SOURCE_FILES_PREFIX}/rendermd2.cpp
	${SOURCE_FILES_PREFIX}/renderparticles.cpp
	${SOURCE_FILES_PREFIX}/rendertext.cpp
	${SOURCE_FILES_PREFIX}/rndmap.cpp
	${SOURCE_FILES_PREFIX}/savegamedemo.cpp
	${SOURCE_FILES_PREFIX}/server.cpp
	${SOURCE_FILES_PREFIX}/serverbrowser.cpp
	${SOURCE_FILES_PREFIX}/serverms.cpp
	${SOURCE_FILES_PREFIX}/serverutil.cpp
	${SOURCE_FILES_PREFIX}/sound.cpp
	${SOURCE_FILES_PREFIX}/tools.cpp
	${SOURCE_FILES_PREFIX}/weapon.cpp
	${SOURCE_FILES_PREFIX}/world.cpp
	${SOURCE_FILES_PREFIX}/worldio.cpp
	${SOURCE_FILES_PREFIX}/worldlight.cpp
	${SOURCE_FILES_PREFIX}/worldocull.cpp
	${SOURCE_FILES_PREFIX}/worldrender.cpp
)

set(SOURCE_SERVER
	${SOURCE_FILES_PREFIX}/serverutil.cpp
	${SOURCE_FILES_PREFIX}/serverms.cpp
	${SOURCE_FILES_PREFIX}/server.cpp
	${SOURCE_FILES_PREFIX}/tools.cpp
)

### includes
set(CUBE_INCL ${OPENGL_INCLUDE_DIR} ${GLUT_INCLUDE_DIRS} ${SDL_INCLUDE_DIR} ${SDL_MIXER_INCLUDE_DIRS} ${SDL_IMAGE_INCLUDE_DIRS} ${ZLIB_INCLUDE_DIRS} enet/include )

### libraries
set(CUBE_LIBS enet ${SDL_LIBRARY} ${SDL_MIXER_LIBRARIES} ${SDL_IMAGE_LIBRARIES} ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES} ${ZLIB_LIBRARIES} ${X11_X11_LIB}  )

### Executables
add_executable(cube_client ${SOURCE_CLIENT})

target_include_directories(cube_client PRIVATE ${CUBE_INCL})

target_link_libraries(cube_client ${CUBE_LIBS})
################################################
################################################
add_executable(cube_server ${SOURCE_SERVER})

target_include_directories(cube_server PRIVATE ${CUBE_INCL})

target_compile_definitions(cube_server PRIVATE STANDALONE)

target_link_libraries(cube_server enet)


