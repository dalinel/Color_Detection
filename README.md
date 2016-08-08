# Color Detection For Collision Avoidance

This program is a color detection program for collision avoidance.
An integrated version with an active node is available on the obstacle_detection_with_lidar branch.

##Setup

###Requirements:

	*opencv 3.0. Should work with other older versions or with opencv 3.1.

###Install:

	*cd "path to the Color_Detection dir"
	*If you don't have a usb webcam change port to 0 in main.cpp line 7
	*mkdir build
	*cd build
	*cmake ..
	*make

###Run :

	*./detect color1 [color2 color3 color4 ...]

###Colors available:

	*red (well adjusted)
	*orange (well adjusted)
	*green
	*yellow
	*purple
	*blue

###Ex :

	* ./detect red orange green
	* ./detect red

## Parameters and adjustments

Parameters to change depending of your camera:

	*int port (main.cpp line 7): set to 0 for the inner camera of the computer and to 1 for an outer camera.

	*int bottomPixelsToCrop (main.cpp line 6) : if you need to crop the bottom part of your image to not detect
	 	it (ex: height in pixel of the visible part of the boat on the image).

	*float webcamAngleApertureX (detectUtility.cpp line 53): the corresponding angle value in radians of one
	 	pixel in the X direction.

	*float webcamAngleApertureY (detectUtility.cpp line 54):  the corresponding angle value in radians of one
	 	pixel in the Y direction.

For a better detection it is almost mandatory to make adjustments on the colors to detect. When the program starts it opens a "Change Detection Values" window with trackbars. For each color you will need to adjust the H, S and V threshold values. If you want to store those new found values you can do it in detectUtility.cpp in the void initHsvColors() function.

The minArea trackbar is setting up the minarea of objects to detect.

You can see the thresholded image in the window "Thresholded Image". What you want to obtain is an image with everything in black excepted the color to detect which will be in white.

## How to find HSV threshold values?

### Best adjustment

To find new H,S,V threshold values put every min trackbar to 0 and every max trackbar to the max available.

Begin by adjusting the lowH trackbar. Increase the value step by step. When you will see the object to detect disappear in black go back a little and settle the highH trackbar.

To settle the highH trackbar,you need to decrease the value step by step. If the object to detect disappear in black, go back and settle the next trackbar.

Do the same for S and V.

You will then have good H, S and V threshold values. Watch out to luminosity, test your values with light and shadow.


### Quick adjustment

Click on the color to detect in the "Detection" Window. H, S and V threshold values
will be adjusted automatically. You can increase the gap between min and max to be able to detect the object with a variation of luminosity.Watch-out to luminosity, test your values with light and shadow.
