# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Import all the necessary modules for the program.

### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:
Using Canny operator from cv2,detect the edges of the image.

### Step5:
Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## Program and Output
### Input image 
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('tiger.jpg')  # Replace with your image path
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/0d494362-b947-4913-8065-32cc3200c42a)

### Grayscale image
```python
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/c4c9a2a9-28e0-4fae-8214-8a4b0c366d88)

### Canny Edge detector output
```python
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/ea441d27-13b5-4556-8fb4-90d88dad6751)

### Display the result of Hough transform
```python
lines = cv2.HoughLinesP(canny_edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=100, maxLineGap=100)
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/59d26d04-f1db-470a-8016-4456a8dffa16)

## Result
Thus,The Python program to detect the lines using Hough Transform run successfully.
