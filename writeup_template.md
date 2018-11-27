Project: Finding Lane Lines on the Road

The goals / steps of this project are the following:

1.Make a pipeline that finds lane lines on the road
2.Reflect on your work in a written report


The Three steps of the writeup is made of

	1.Pipeline Description
	2.Finding Potential shortcoming
	3.Possible Improvements

1.Pipeline Description

My pipeline consisted of below steps

	1. Read the image as frame by frame from video to process it.
	2. Preprocess the image by following steps
		2.1 convert the RGB image from the video to grey scale
		2.2 Perform	Gaussian Blur to the image
		2.3 Perfrom Canny Edge Detection
		2.4 Perform Region of masking to focus on lanes and not objects
		2.5 Perform Hough Transform to draw lines on our specified condition
		
			Here with the help of HoughLinesP the coordinates of the lines were found.
			Then for the left side of the lane i found the (minX,maxY) and (maxX,minY)
			
			now with the help of two equations maxY=minX*m+c and minY=maxX*m+c , i found m and c
			
			Then on substituting y=0 and values of m and c obtained from the above equations, i found the intercept with x axis.
			using the coordinates of the intersect and (maxX,minY), we draw a line segment of them.
			
			The same thing is done of the right side of the lane.
		2.6 The final image required is obtained
	3. Then the processd image is fed on the output video frame by frame
			


2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road is curved. 
As the region of masking might not have the right end curve of the white line fully. The lane detection will not be perfect

Another shortcoming could be a car inside the region masking.
Since its edges will also be considered as there are changes few points of it might fall in the Hough space.
Then the line drawing will be improper


3. Suggest possible improvements to your pipeline

A possible improvement would be to train a Deep Neural Network to identify objects like car and lane.
Insted of depending on the Hough Transform to perdict the line points which is high non-relaiable.

With the help of a well trained classifer model of Convolutional Neural Network we can identify various objects in the image which can help has make better prediction.



