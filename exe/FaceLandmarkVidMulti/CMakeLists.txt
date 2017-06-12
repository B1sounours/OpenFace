# Target			
add_executable(FaceLandmarkVidMulti FaceLandmarkVidMulti.cpp)
target_link_libraries(FaceLandmarkVidMulti PRIVATE
	FaceAnalyser
)

# Installations
install(TARGETS FaceLandmarkVidMulti
		EXPORT open_face-targets
		DESTINATION bin COMPONENT exe)