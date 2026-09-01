# SEC-DIP--Coin-Detection-using-OpenCV-in-Python
# Aim:
To develop an AI-based image processing system that can automatically detect and count coins in an image using Python and OpenCV, while visualizing all the intermediate processing steps such as grayscale conversion, blurring, edge detection, and contour detection.

# OBJECTIVE:

1. To apply fundamental computer vision techniques to identify circular objects (coins).

2. To understand the use of image preprocessing and feature extraction using OpenCV.

3. To display all intermediate outputs to explain how detection is achieved.

4. To count and label the number of coins accurately.

# ALGORITHM:
1. Start

2. Input the image (coins image file).

3. Convert the image to grayscale to simplify analysis.

4. Apply Gaussian Blur to reduce image noise and smooth edges.

5. Apply Canny Edge Detection to find edges of coins.

6. Find Contours in the edge-detected image.

7. Filter Contours based on area (to remove small noise).

8.Draw circles around detected coins and assign serial numbers.

9.Count the total number of coins detected.

10. End.

# Program:
```
import cv2
import matplotlib.pyplot as plt

img = cv2.imread("coins.png")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Detect coins
circles = cv2.HoughCircles(
    gray,
    cv2.HOUGH_GRADIENT,
    dp=1.2,
    minDist=40,
    param1=100,
    param2=40,
    minRadius=20,
    maxRadius=100
)

# Draw one rectangle around each coin
if circles is not None:
    circles = circles[0].astype(int)

    for x, y, r in circles:
        cv2.rectangle(
            img,
            (x - r, y - r),
            (x + r, y + r),
            (0, 255, 0),
            2
        )

# Display
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Coin Detection")
plt.axis("off")
plt.show()

```
### Output :
<img width="423" height="402" alt="image" src="https://github.com/user-attachments/assets/830c6fc7-591b-450e-94d2-5dea986ce2b8" />
### Result :
The system successfully detected all coins in the given image.
