
# Ex-7 : Detect-the-lines-using-Hough-Transform

## Developed By
Name: YOGESH S

Register No: 212224230311

## Aim
To implement a basic lane detection pipeline using OpenCV by completing missing code segments at specified locations.

## Learning Objective
* Understand each stage of image processing
* Learn how to build a complete computer vision pipeline
* Practice writing code in guided sections

## Software Used
* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

## Algorithm & Explanation

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load the image using imread() from cv2 module
image = cv2.imread(r"C:\Users\admin\Question bank for college\Sem 5 subs\second half (16 credits)\chessboardbrown.jpeg")  # Replace 'image.jpg' with your image path

# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')

# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150

# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')

# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)

# Step 6: Using a for loop, draw the lines on the original image using the detected coordinates
# The lines variable contains the endpoints of the detected lines
for line in lines:
    x1, y1, x2, y2 = line  # Unpacking the line coordinates
    cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)  # Draw green lines with thickness of 2

# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Image with lines drawn
plt.title("Result of Hough Transform")
plt.axis('off')

```

## Output
### Original image
<br>
<img width="596" height="498" alt="image" src="https://github.com/user-attachments/assets/7f3607af-a33c-4c8a-ad4d-aaf697c658eb" />


### Greyscale image
<br>
<img width="581" height="500" alt="image" src="https://github.com/user-attachments/assets/8162ab80-55ec-4981-8db6-48b6c74b44e7" />


### Canny edge detector
<br>
<img width="582" height="501" alt="image" src="https://github.com/user-attachments/assets/edee857b-ac10-4b61-ac46-4f2383bb4f61" />


### Hough Transform
<br>
<img width="582" height="510" alt="image" src="https://github.com/user-attachments/assets/72a9bc89-57b7-40c2-b0ee-21e493b51155" />



## Result
Thus, the lane detection pipeline is successfully implemented by completing the missing code sections. The system detects and highlights lane lines effectively.
