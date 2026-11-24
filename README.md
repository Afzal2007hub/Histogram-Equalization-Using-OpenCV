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
~~~
import cv2
import numpy as np
import matplotlib.pyplot as plt

print("OpenCV Version:", cv2.__version__)
print("Libraries imported successfully!")
~~~

~~~
gray = cv2.imread("nature.png", cv2.IMREAD_GRAYSCALE)

if gray is None:
    raise FileNotFoundError(
        "Image not found. Check the filename and notebook folder."
    )

print("Image dimensions:", gray.shape)

plt.figure(figsize=(6, 6))
plt.imshow(gray, cmap="gray")
plt.title("Nature - Grayscale Image")
plt.axis("off")
plt.show()
~~~


~~~
plt.figure(figsize=(8, 4))

plt.hist(gray.ravel(), bins=256, range=(0, 256))
plt.title("Histogram of Grayscale Image")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")
plt.show()

~~~

~~~
equalized = cv2.equalizeHist(gray)

plt.figure(figsize=(6, 6))
plt.imshow(equalized, cmap="gray")
plt.title("Nature - Histogram Equalized")
plt.axis("off")
plt.show()

~~~

~~~
plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(gray, cmap="gray")
plt.title("Original Grayscale Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.hist(gray.ravel(), bins=256, range=(0, 256))
plt.title("Original Histogram")
plt.xlabel("Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 3)
plt.imshow(equalized, cmap="gray")
plt.title("Equalized Image")
plt.axis("off")

plt.subplot(2, 2, 4)
plt.hist(equalized.ravel(), bins=256, range=(0, 256))
plt.title("Equalized Histogram")
plt.xlabel("Intensity")
plt.ylabel("Frequency")

plt.tight_layout()
plt.show()
~~~

~~~
color = cv2.imread("nature.png")

if color is None:
    raise FileNotFoundError("Check your image filename.")

rgb = cv2.cvtColor(color, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(6, 6))
plt.imshow(rgb)
plt.title("Nature - Original Color Image")
plt.axis("off")
plt.show()
~~~

~~~
b, g, r = cv2.split(color)

plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(rgb)
plt.title("Original Color Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.hist(b.ravel(), bins=256, range=(0, 256))
plt.title("Blue Channel Histogram")
plt.xlabel("Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 3)
plt.hist(g.ravel(), bins=256, range=(0, 256))
plt.title("Green Channel Histogram")
plt.xlabel("Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 4)
plt.hist(r.ravel(), bins=256, range=(0, 256))
plt.title("Red Channel Histogram")
plt.xlabel("Intensity")
plt.ylabel("Frequency")

plt.tight_layout()
plt.show()

~~~

~~~
blue = cv2.merge([b, np.zeros_like(b), np.zeros_like(b)])
green = cv2.merge([np.zeros_like(g), g, np.zeros_like(g)])
red = cv2.merge([np.zeros_like(r), np.zeros_like(r), r])

fig, axes = plt.subplots(1, 3, figsize=(15, 5))

axes[0].imshow(cv2.cvtColor(blue, cv2.COLOR_BGR2RGB))
axes[0].set_title("Blue Channel")

axes[1].imshow(cv2.cvtColor(green, cv2.COLOR_BGR2RGB))
axes[1].set_title("Green Channel")

axes[2].imshow(cv2.cvtColor(red, cv2.COLOR_BGR2RGB))
axes[2].set_title("Red Channel")

for ax in axes:
    ax.axis("off")

plt.tight_layout()
plt.show()

~~~
### Developed By:
**Name:** Mohamed Afzal N 

### Register No: 212225220065  

---


##  Output


<img width="484" height="329" alt="image" src="https://github.com/user-attachments/assets/5b8ab968-540c-4aa0-bf4e-95da09d97c63" />
<img width="713" height="391" alt="image" src="https://github.com/user-attachments/assets/98985e07-68ea-497b-8172-f3ad926f4d2b" />
<img width="484" height="329" alt="image" src="https://github.com/user-attachments/assets/cba23ec1-4962-446f-b2ab-81baf96f48d6" />
<img width="1013" height="307" alt="image" src="https://github.com/user-attachments/assets/bdd6d01f-717c-4339-bfa7-ac773f31644a" />
<img width="988" height="326" alt="image" src="https://github.com/user-attachments/assets/3a59372e-5a7f-4eaf-95ed-336527e438b9" />
<img width="484" height="329" alt="image" src="https://github.com/user-attachments/assets/83281946-f2ec-45e8-85c1-1b88df32315e" />
<img width="933" height="316" alt="image" src="https://github.com/user-attachments/assets/e9d113a6-9769-465f-8251-9c88277bf07b" />
<img width="986" height="337" alt="image" src="https://github.com/user-attachments/assets/a73b627f-d507-4b50-a87e-cfe485fa9dd3" />

<img width="995" height="218" alt="image" src="https://github.com/user-attachments/assets/11554666-96fa-4190-befd-22464b3d7a6b" />



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
