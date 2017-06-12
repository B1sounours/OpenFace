# Target			
add_executable(FeatureExtraction FeatureExtraction.cpp)
target_link_libraries(FeatureExtraction PRIVATE
	FaceAnalyser
)

# Installations
install(TARGETS FeatureExtraction
		EXPORT open_face-targets
		DESTINATION bin COMPONENT exe)