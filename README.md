# COIN DETECTION USING OPENCV
## Name: Ashwath M
## Register number: 212223230023

## AIM:
To detect and count the number of coins present in an image using image processing techniques such as grayscale conversion, thresholding, morphological operations, and blob detection with OpenCV.

## SOFTWARE REQUIREMENTS:
- Python 3.x
- OpenCV (cv2)
- NumPy
- Matplotlib
- Jupyter Notebook or any Python IDE

## ALGORITHM:
1. Read the Image: Load the coin image using cv2.imread().
2. Convert to Grayscale: Convert the color image to grayscale for easier processing.
3. Apply Thresholding: Convert the grayscale image into a binary image to separate coins from the background.
4. Perform Morphological Operations: Use dilation and erosion to remove noise and enhance coin boundaries.
5. Detect Blobs: Apply the SimpleBlobDetector to identify circular regions corresponding to coins and count them.

## PROGRAM:
```
import cv2
import matplotlib.pyplot as plt
import numpy as np

image = cv2.imread('Coins.png')

imageCopy = image.copy()
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.show()

imageGray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.figure(figsize=(10,10))
plt.subplot(121);plt.imshow(image[:,:,::-1]);plt.title("Original Image")
plt.subplot(122); plt.imshow(imageGray,cmap='gray');plt.title("Grayscale Image"); plt.show()

imageB, imageG, imageR = cv2.split(image)

plt.figure(figsize=(20,12))
plt.subplot(141);plt.imshow(image[:,:,::-1]);plt.title("Original Image")
plt.subplot(142);plt.imshow(imageB,cmap='gray');plt.title("Blue Channel")
plt.subplot(143);plt.imshow(imageG,cmap='gray');plt.title("Green Channel")
plt.subplot(144);plt.imshow(imageR,cmap='gray');plt.title("Red Channel");
plt.show()

_, thresh = cv2.threshold(imageG, 80, 255, cv2.THRESH_BINARY)

plt.imshow(thresh, cmap='gray');plt.title('Thresholded Image');plt.show()

kernel = np.ones((3, 3), np.uint8)
dilate = cv2.dilate(thresh, kernel, iterations=2)

plt.imshow(dilate,cmap='gray')
plt.title("Dilated Image")
plt.show()

kernel1 = np.ones((5, 5), np.uint8)

eroded = cv2.erode(dilate, kernel1, iterations=1)
plt.imshow(eroded,cmap='gray')
plt.title("Eroded Image")
plt.show()

params = cv2.SimpleBlobDetector_Params()

params.blobColor = 0

params.minDistBetweenBlobs = 2

params.filterByArea = False

params.filterByCircularity = True
params.minCircularity = 0.8

params.filterByConvexity = True
params.minConvexity = 0.8

params.filterByInertia =True
params.minInertiaRatio = 0.8

detector = cv2.SimpleBlobDetector_create(params)

keypoints = detector.detect(eroded)

num_coins = len(keypoints)
print(f"Number of coins detected: {num_coins}")
```
## OUTPUT:

<img width="1026" height="521" alt="image" src="https://github.com/user-attachments/assets/021fd4a3-4090-44e1-819a-e8dc9d1f6172" />

<img width="1242" height="331" alt="image" src="https://github.com/user-attachments/assets/008f0d19-c910-45d2-9a45-63a80142a52d" />

<img width="487" height="491" alt="image" src="https://github.com/user-attachments/assets/c33efc07-b57f-4335-b842-8ae05e6b0396" />

<img width="474" height="491" alt="image" src="https://github.com/user-attachments/assets/d9830edc-c4ae-42bb-a8dc-e0f7568d98d5" />

<img width="469" height="499" alt="image" src="https://github.com/user-attachments/assets/917b524c-11c4-4ed9-9195-6689e42f7e76" />

<img width="282" height="28" alt="image" src="https://github.com/user-attachments/assets/8c716824-8757-45b9-a667-e518f4a1e260" />






## RESULT:
- The program successfully detects and counts 9 coins in the input image.
- Each detected coin is highlighted with a red circle on the output image.
