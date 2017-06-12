# Target			
add_executable(FaceLandmarkVid FaceLandmarkVid.cpp)
target_link_libraries(FaceLandmarkVid PRIVATE
	FaceAnalyser
)

# Installations
install(TARGETS FaceLandmarkVid
		EXPORT open_face-targets
		DESTINATION bin COMPONENT exe)