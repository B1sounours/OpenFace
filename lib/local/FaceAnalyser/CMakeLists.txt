# Source
SET(SOURCE
    src/Face_utils.cpp
	src/FaceAnalyser.cpp
	src/SVM_dynamic_lin.cpp
	src/SVM_static_lin.cpp
	src/SVR_dynamic_lin_regressors.cpp
	src/SVR_static_lin_regressors.cpp
	src/GazeEstimation.cpp
)

SET(HEADERS
    include/Face_utils.h	
	include/FaceAnalyser.h
	include/SVM_dynamic_lin.h
	include/SVM_static_lin.h
	include/SVR_dynamic_lin_regressors.h
	include/SVR_static_lin_regressors.h
	include/GazeEstimation.h
)

#include_directories(./include)
#include_directories(${FACEANALYSER_SOURCE_DIR}/include)
#include_directories(../LandmarkDetector/include)

# Target
add_library(FaceAnalyser ${SOURCE} ${HEADERS})
target_include_directories(FaceAnalyser PUBLIC
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
	${Boost_INCLUDE_DIRS}
	${OpenCV_INCLUDE_DIRS}
	${dlib_INCLUDE_DIRS}
	${TBB_INCLUDE_DIRS}
)
target_link_libraries(FaceAnalyser PUBLIC
	LandmarkDetector
	${Boost_LIBRARIES}
	${OpenCV_LIBS}
	${dlib_LIBRARIES}
	${TBB_LIBRARIES}
)

# Installations
install(TARGETS FaceAnalyser EXPORT open_face-targets DESTINATION lib)
install(FILES ${HEADERS} DESTINATION include/OpenFace)