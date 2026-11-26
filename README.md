# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:
**Name:** LINGESH D

### Register No:
212225230151

---
## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
```
image = cv2.imread(r"C:\Users\acer\Downloads\baseball.jpeg.jpeg")
image.shape
```
## Output
<img width="595" height="102" alt="Screenshot 2026-11-18 152808" src="https://github.com/user-attachments/assets/20e4b146-0c46-45a8-9c25-5d3e0db6c03f" />

## Program
```
# Display the image using Matplotlib

plt.imshow(image[:,:,::-1])
plt.title('Original Image')
plt.show()

```
## Output
<img width="976" height="495" alt="Screenshot 2026-11-18 153224" src="https://github.com/user-attachments/assets/2f2e37c4-c133-46a0-8766-6823902f9311" />

## Program
```
tx, ty = 100, 200
M_translation = np.float32([[1, 0, tx],[0, 1, ty]])
translated_image = cv2.warpAffine(image, M_translation,(image.shape[1], image.shape[0]))
```
```
plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(translated_image[:,:,::-1])
plt.title("Translated Image")
plt.axis("off")

plt.show()
```
## Output
<img width="1237" height="362" alt="Screenshot 2026-11-18 153354" src="https://github.com/user-attachments/assets/5528b128-6531-4cf1-a7a5-f276fb2595a4" />

## Program
```
image = cv2.imread(r"C:\Users\acer\Downloads\baseball.jpeg.jpeg")
downscaled_image = cv2.resize(image, None,fx=0.25,fy=0.25,interpolation=cv2.INTER_LINEAR)
upscaled_image = cv2.resize(image, None,fx=3,fy=3,interpolation=cv2.INTER_LINEAR)
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(downscaled_image[:,:,::-1])
plt.title("Downscaled Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(upscaled_image[:,:,::-1])
plt.title("Upscaled Image")
plt.axis("off")

plt.show()
```
## Output
<img width="1370" height="288" alt="Screenshot 2026-11-18 153507" src="https://github.com/user-attachments/assets/f584debf-b8a9-49d0-9e13-ff51adac3453" />

## Program
```
horizontal_matrix = np.float32([[1,0.5,0],[0,1,0]])
horizontal_shear = cv2.warpAffine(image,horizontal_matrix,(image.shape[1], image.shape[0]))
vertical_matrix = np.float32([[1,0,0],[0.5,1,0]])
vertical_shear = cv2.warpAffine(image,vertical_matrix,(image.shape[1], image.shape[0]))
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(horizontal_shear[:,:,::-1])
plt.title("Horizontal Shear")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(vertical_shear[:,:,::-1])
plt.title("Vertical Shear")
plt.axis("off")

plt.show()
```
## Output
<img width="1486" height="298" alt="Screenshot 2026-11-18 153709" src="https://github.com/user-attachments/assets/fe9ad966-126e-4fb2-94ee-c5e8d261b930" />

## Program
```
horizontal = cv2.flip(image,1)
vertical = cv2.flip(image,0)
both = cv2.flip(image,-1)
```
```
plt.figure(figsize=(10,10))

plt.subplot(2,2,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,2,2)
plt.imshow(horizontal[:,:,::-1])
plt.title("Horizontal Reflection")
plt.axis("off")

plt.subplot(2,2,3)
plt.imshow(vertical[:,:,::-1])
plt.title("Vertical Reflection")
plt.axis("off")

plt.subplot(2,2,4)
plt.imshow(both[:,:,::-1])
plt.title("Both Axes Reflection")
plt.axis("off")

plt.show()
```
## Output
<img width="1341" height="435" alt="Screenshot 2026-11-18 153822" src="https://github.com/user-attachments/assets/73d6cfe0-00e2-4a9a-a97b-7157525d3fd4" />

<img width="1273" height="462" alt="Screenshot 2026-11-18 153844" src="https://github.com/user-attachments/assets/0a8ca9c5-b024-4059-97b1-8e7269c523c3" />

## Program
```
(height, width) = image.shape[:2]

center = (width//2, height//2)
```
```
matrix45 = cv2.getRotationMatrix2D(center,45,1)
rotate45 = cv2.warpAffine(image,matrix45,(width,height))
```
```
matrix90 = cv2.getRotationMatrix2D(center,90,1)
rotate90 = cv2.warpAffine(image,matrix90,(width,height))
```
```
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(rotate45[:,:,::-1])
plt.title("45 Degree Rotation")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(rotate90[:,:,::-1])
plt.title("90 Degree Rotation")
plt.axis("off")

plt.show()
```
## Output
<img width="1432" height="295" alt="Screenshot 2026-11-18 154013" src="https://github.com/user-attachments/assets/e6be7b66-02bc-4ea4-824a-a214eef3ea1b" />


##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
