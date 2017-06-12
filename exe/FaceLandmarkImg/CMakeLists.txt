# Target			
add_executable(FaceLandmarkImg FaceLandmarkImg.cpp)
target_link_libraries(FaceLandmarkImg PRIVATE
	FaceAnalyser
)

# Installations
install(TARGETS FaceLandmarkImg
		EXPORT open_face-targets
		DESTINATION bin COMPONENT exe)