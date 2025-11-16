# COIN DETECTION USING OPENCV

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

## OUTPUT:
- The program successfully detects and counts 9 coins in the input image.
- Each detected coin is highlighted with a red circle on the output image.
