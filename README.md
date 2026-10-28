# EXP-3-Record-Histogram-processing
---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read grayscale image
gray = cv2.imread('parrot.jpg', 0)

if gray is None:
    print("Image not found!")
    exit()

# Histogram equalization
equalized = cv2.equalizeHist(gray)

# Display grayscale images and histograms
plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(gray, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis('off')

plt.subplot(2, 2, 2)
plt.hist(gray.ravel(), 256, [0, 256])
plt.title("Original Histogram")

plt.subplot(2, 2, 3)
plt.imshow(equalized, cmap='gray')
plt.title("Equalized Image")
plt.axis('off')

plt.subplot(2, 2, 4)
plt.hist(equalized.ravel(), 256, [0, 256])
plt.title("Equalized Histogram")

plt.tight_layout()
plt.show()

# Read color image
img = cv2.imread('parrot.jpg')

if img is None:
    print("Image not found!")
    exit()

# Split B, G, R channels
b, g, r = cv2.split(img)

plt.figure(figsize=(10, 4))
plt.hist(b.ravel(), 256, [0, 256], color='blue', alpha=0.5)
plt.hist(g.ravel(), 256, [0, 256], color='green', alpha=0.5)
plt.hist(r.ravel(), 256, [0, 256], color='red', alpha=0.5)
plt.title("BGR Channel Histograms")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")
plt.show()

# Convert BGR to HSV
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)

# Equalize Value channel
v_eq = cv2.equalizeHist(v)

# Merge and convert back to BGR
hsv_eq = cv2.merge((h, s, v_eq))
enhanced = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)

# Display color images and histograms
plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Color Image")
plt.axis('off')

plt.subplot(2, 2, 2)
plt.hist(img.ravel(), 256, [0, 256])
plt.title("Original Color Histogram")

plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(enhanced, cv2.COLOR_BGR2RGB))
plt.title("Enhanced Color Image")
plt.axis('off')

plt.subplot(2, 2, 4)
plt.hist(enhanced.ravel(), 256, [0, 256])
plt.title("Enhanced Color Histogram")

plt.tight_layout()
plt.show()
```

### Developed By:
**Name:** INFANT VIJAY A 

### Register No: 212225240052

---

##  Output
<img width="1325" height="486" alt="Screenshot 2026-10-28 180149" src="https://github.com/user-attachments/assets/830c1424-0eb7-4084-af52-1e2bc7cb0f64" />

<img width="1308" height="517" alt="Screenshot 2026-10-28 180230" src="https://github.com/user-attachments/assets/0e0ab500-90ac-4211-a082-c5699b5e2451" />

<img width="1057" height="488" alt="Screenshot 2026-10-28 180331" src="https://github.com/user-attachments/assets/67891f2c-6d7c-4369-9a03-4863042076e9" />

<img width="1137" height="901" alt="Screenshot 2026-10-28 180431" src="https://github.com/user-attachments/assets/52e62cb8-3487-45ef-8daa-0878b3e2daf8" />

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
