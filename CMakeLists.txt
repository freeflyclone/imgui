project(imgui)

set(PROJ_NAME imgui)
set(PROJ_FOLDER ${CMAKE_CURRENT_SOURCE_DIR})

set(HEADERS
    ${PROJ_FOLDER}/imconfig.h
    ${PROJ_FOLDER}/imgui.h
    ${PROJ_FOLDER}/imgui_internal.h
    ${PROJ_FOLDER}/imstb_rectpack.h
    ${PROJ_FOLDER}/imstb_textedit.h
    ${PROJ_FOLDER}/imstb_truetype.h
)	

set(SOURCES
    ${PROJ_FOLDER}/imgui.cpp
    ${PROJ_FOLDER}/imgui_demo.cpp
    ${PROJ_FOLDER}/imgui_draw.cpp
    ${PROJ_FOLDER}/imgui_tables.cpp
    ${PROJ_FOLDER}/imgui_widgets.cpp
    ${PROJ_FOLDER}/backends/imgui_impl_opengl3.cpp
    ${PROJ_FOLDER}/backends/imgui_impl_glfw.cpp
)

add_library(${PROJ_NAME} ${SOURCES} ${HEADERS})
set_target_properties(
    ${PROJ_NAME} 
  PROPERTIES
    FOLDER "xclass/libs/3rdParty"
	# set for static runtime 
	MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>"
)

set(PROJ_HEADER_DIRECTORIES 
    ${PROJ_FOLDER}
    ${PROJ_FOLDER}/backends
    ${PROJ_FOLDER}/../../xgl/inc
    ${PROJ_FOLDER}/../../3rdParty/glfw/include
)

target_include_directories(${PROJ_NAME} PRIVATE ${PROJ_HEADER_DIRECTORIES})
