# Histogram Equalization Using OpenCV (Grayscale & Color Images)

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
import matplotlib.pyplot as plt
import numpy as np

# Step 1: Import required libraries (OpenCV, NumPy, and Matplotlib)

# Step 2: Read the image 'test.jpg' in grayscale format
img_gray = cv2.imread("test.jpg", cv2.IMREAD_GRAYSCALE)

# Step 3 & 4: Apply histogram equalization using cv2.equalizeHist() to enhance contrast
img_equalized_gray = cv2.equalizeHist(img_gray)

# Step 5: Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 x 2 grid
plt.figure(figsize=(10, 10))

# Subplot 1: Original Grayscale Image
plt.subplot(2, 2, 1)
plt.imshow(img_gray, cmap="gray")
plt.title("Original Grayscale Image")
plt.axis("off")

# Subplot 2: Histogram of Original Image
plt.subplot(2, 2, 2)
plt.hist(img_gray.ravel(), bins=256, range=(0, 256), color="black")
plt.title("Histogram (Original)")

# Subplot 3: Enhanced Grayscale Image (Equalized)
plt.subplot(2, 2, 3)
plt.imshow(img_equalized_gray, cmap="gray")
plt.title("Enhanced Image (Equalized)")
plt.axis("off")

# Subplot 4: Histogram of Enhanced Image
plt.subplot(2, 2, 4)
plt.hist(img_equalized_gray.ravel(), bins=256, range=(0, 256), color="black")
plt.title("Histogram (Equalized)")

plt.tight_layout()
plt.show()

# Step 6: Read the same image in color format
img_color = cv2.imread("test.jpg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB)

# Step 7: Split the image into B, G, R channels and plot their histograms
b, g, r = cv2.split(img_color)

plt.figure(figsize=(12, 4))
plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Color Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.hist(b.ravel(), bins=256, range=(0, 256), color="blue", alpha=0.6, label="B channel")
plt.hist(g.ravel(), bins=256, range=(0, 256), color="green", alpha=0.6, label="G channel")
plt.hist(r.ravel(), bins=256, range=(0, 256), color="red", alpha=0.6, label="R channel")
plt.title("RGB Histograms")
plt.xlabel("Bin Value")
plt.ylabel("Pixel Count")
plt.legend()
plt.tight_layout()
plt.show()

# Step 8: Convert the image from BGR to HSV color space
img_hsv = cv2.cvtColor(img_color, cv2.COLOR_BGR2HSV)

# Step 9: Apply histogram equalization on the V (Value) channel
h, s, v = cv2.split(img_hsv)
v_equalized = cv2.equalizeHist(v)

# Step 10: Merge the channels and convert the image back to BGR format
img_hsv_merged = cv2.merge((h, s, v_equalized))
img_enhanced_bgr = cv2.cvtColor(img_hsv_merged, cv2.COLOR_HSV2BGR)
img_enhanced_rgb = cv2.cvtColor(img_enhanced_bgr, cv2.COLOR_HSV2RGB)

# Step 11: Display original color image, histogram, enhanced image, and enhanced histogram using a 2 x 2 grid
plt.figure(figsize=(10, 10))

# Subplot 1: Original Color Image
plt.subplot(2, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Color Image")
plt.axis("off")

# Subplot 2: Histogram of Original Image (using grayscale representation)
plt.subplot(2, 2, 2)
plt.hist(img_gray.ravel(), bins=256, range=(0, 256), color="black")
plt.title("Histogram (Original)")
plt.xlabel("Bin Value")
plt.ylabel("Pixel Count")

# Subplot 3: Enhanced Color Image (HSV V-equalized)
plt.subplot(2, 2, 3)
plt.imshow(img_enhanced_rgb)
plt.title("Enhanced Color Image (HSV V-equalized)")
plt.axis("off")

# Subplot 4: Histogram of Enhanced Image (equalized V channel)
plt.subplot(2, 2, 4)
plt.hist(v_equalized.ravel(), bins=256, range=(0, 256), color="black")
plt.title("Histogram (Enhanced)")
plt.xlabel("Bin Value")
plt.ylabel("Pixel Count")

plt.tight_layout()
plt.show()
```

### Developed By:
**Name:** ESWAR S

**Register No:** 212225230067

---

##  Output

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  
![alt text](image.png)

### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  
![alt text](image-2.png)
![alt text](image-1.png)
---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.