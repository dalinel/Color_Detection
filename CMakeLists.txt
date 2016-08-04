cmake_minimum_required(VERSION 2.8)
project( detect )
find_package( OpenCV REQUIRED )
add_executable( detect main.cpp detectUtility.cpp detectUtility.h)
target_link_libraries( detect ${OpenCV_LIBS} )

