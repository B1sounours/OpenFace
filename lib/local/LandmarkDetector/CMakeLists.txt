# Source
SET(SOURCE
    src/CCNF_patch_expert.cpp
	src/LandmarkDetectionValidator.cpp
    src/LandmarkDetectorFunc.cpp
	src/LandmarkDetectorModel.cpp
    src/LandmarkDetectorUtils.cpp
	src/LandmarkDetectorParameters.cpp
	src/Patch_experts.cpp
	src/PAW.cpp
    src/PDM.cpp
	src/SVR_patch_expert.cpp
	src/stdafx.cpp
)

SET(HEADERS
    include/CCNF_patch_expert.h	
    include/LandmarkCoreIncludes.h
	include/LandmarkDetectionValidator.h
    include/LandmarkDetectorFunc.h
	include/LandmarkDetectorModel.h
	include/LandmarkDetectorParameters.h
	include/LandmarkDetectorUtils.h
	include/Patch_experts.h	
    include/PAW.h
	include/PDM.h
	include/SVR_patch_expert.h		
	include/stdafx.h
)

#include_directories(./include)
#include_directories(${LandmarkDetector_SOURCE_DIR}/include)

# Target
add_library(LandmarkDetector ${SOURCE} ${HEADERS})
target_include_directories(LandmarkDetector PUBLIC
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
	${Boost_INCLUDE_DIRS}
	${OpenCV_INCLUDE_DIRS}
	${dlib_INCLUDE_DIRS}
	${TBB_INCLUDE_DIRS}
)
target_link_libraries(LandmarkDetector PUBLIC
	${Boost_LIBRARIES}
	${OpenCV_LIBS}
	${dlib_LIBRARIES}
	${TBB_LIBRARIES}
)

if(WIN32)
	target_compile_definitions(LandmarkDetector PUBLIC -D_WIN32_WINNT=0x0A00)
endif()

# Installations
install(TARGETS LandmarkDetector EXPORT open_face-targets DESTINATION lib)
install(FILES ${HEADERS} DESTINATION include/OpenFace)
