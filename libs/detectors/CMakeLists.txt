if(CMAKE_MRPT_HAS_OPENCV)
	include_directories(${OpenCV_INCLUDE_DIR} ${OpenCV_INCLUDE_DIRS} ${OPENCV_INCLUDE_DIRS} ${OPENCV_INCLUDEDIR})
endif()

#---------------------------------------------
# Macro declared in "DeclareMRPTLib.cmake":
#---------------------------------------------
define_mrpt_lib(
	# Lib name
	detectors
	# Deps:
	mrpt-gui
	mrpt-slam
	)

if(NOT BUILD_mrpt-detectors)
	return()
endif()

if(CMAKE_MRPT_HAS_OPENCV)
	target_link_libraries(detectors PRIVATE imp_opencv)
endif()

target_link_libraries(detectors PRIVATE Threads::Threads)
