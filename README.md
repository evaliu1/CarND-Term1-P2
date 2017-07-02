# Traffic Sign Classification

## Eva Liu

Traffic Sign Classification

The goals / steps of this project are the following:

1. Dataset Exploration

My pipeline consisted of 5 steps. First, I converted the images to grayscale. Second, I changed the pictures to Gaussian blur. Third, I applied the Canny transform using blurred image from Gaussian sub-function. Fourth, I created masked edges image. Last, I used the Hough transform based on predefined parameters.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding a list of subfunctions. And make sure that there are only four points defined when I started drawing the line. "for line in lines: for x1,y1,x2,y2 in line: cv2.line(line_image, (x1, y1), (x2, y2), color, thickness)"

Inside my project1.ipynb file, I included one picture which shows how my pipeline works.

2. Design and Test a Model Architecture

One potential shortcoming would be what would happen when rode condition is different, our current parameters for sub-functions are not perfectly matching for new road.

Another shortcoming could be the program cannot identify stop line.

3. Test a Model on New Images

A possible improvement would be to make the parameters inside each sub-function changeable.

Another potential improvement could be to draw the third line as the stop line.
