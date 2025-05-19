# OPENING--AND-CLOSING
### Aim
To implement Opening and Closing using Python and OpenCV.

### Software Required
1. Anaconda - Python 3.7
2. OpenCV
   
### Algorithm:
#### Step1:
Create a white image of specified size and add black text ("Sam") to it using cv2.putText.
#### Step2:
Add random salt-and-pepper noise to the image by setting random pixels to black or white.
#### Step3:
Create a smaller structuring element (kernel) of size 5x5 using np.ones().
### Step4:
Apply the Opening operation using cv2.morphologyEx() with erosion followed by dilation.
### Step5:
Apply the Closing operation using cv2.morphologyEx() with dilation followed by erosion.

## Program:
## Import the necessary packages
```
import cv2
import numpy as np
from matplotlib import pyplot as plt
```
## Create the Text using cv2.putText
```
img = np.ones((300, 600), dtype="uint8") * 255  # Create a white image
cv2.putText(img, 'SANJAY', (150, 150), cv2.FONT_HERSHEY_SIMPLEX, 3, (0, 0, 0), 5)  # Add black text 'Sam'
noise = np.random.rand(*img.shape)
img[noise < 0.05] = 0  # Random black pixels (salt)
img[noise > 0.95] = 255  # Random white pixels (pepper)
kernel = np.ones((5, 5), np.uint8)  # A smaller 5x5 square kernel
opening = cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)
closing = cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel)
plt.figure(figsize=(12, 8))
```
## Original image with noise
```
plt.subplot(1, 3, 1)
plt.title('Original Image with Noise')
plt.imshow(img, cmap='gray')
plt.axis('off')
```
## Opening image
```
plt.subplot(1, 3, 2)
plt.title('Opening Operation')
plt.imshow(opening, cmap='gray')
plt.axis('off')
```
## Closing image
```
plt.subplot(1, 3, 3)
plt.title('Closing Operation')
plt.imshow(closing, cmap='gray')
plt.axis('off')

plt.show()
```
## Output:
### Display the input Image
![image](https://github.com/user-attachments/assets/133abaa8-ff21-4be9-9282-bad7a8aa0ae4)

### Display the result of Opening
![image](https://github.com/user-attachments/assets/73e8d858-5066-4692-a293-265e44a09e19)

### Display the result of Closing
![image](https://github.com/user-attachments/assets/afb0b301-5d29-4c95-9f9f-a73741f52658)


## Result
Thus the Opening and Closing operation is used in the image using python and OpenCV.
