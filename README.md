# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** Madhu Mitha V  
- **Register Number:** 2305002013

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread("eagle.png.jpeg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

```
#### 2. Print the image width, height & Channel.
```
img.shape
```
#### 3. Display the image using matplotlib imshow().
```
plt.imshow(img_rgb)
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
cv2.imwrite("eagle.png.jpeg", img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
img = cv2.imread("eagle.png.jpeg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
plt.imshow(img_rgb)
plt.show()
img.shape

```
#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
crop = img_rgb[100:600, 200:900]

plt.imshow(crop)
plt.title("Cropped Region")
plt.axis("off")
plt.show()

crop.shape
```
#### 8. Resize the image up by a factor of 2x.
```
res = cv2.resize(crop, (400, 400))
```
#### 9. Flip the cropped/resized image horizontally.
```
flip = cv2.flip(res, 1)

plt.imshow(flip)
plt.title("Flipped Horizontally")
plt.axis("off")
```

#### 10. Read in the image ('eagle.jpg').
```
img = cv2.imread("eagle.png.jpeg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
text = cv2.putText(img_rgb, "Eagle Image", (200, 700),
                   cv2.FONT_HERSHEY_SIMPLEX, 1,
                   (255, 255, 255), 2)

plt.imshow(text)
plt.title("New Image")
plt.show()
```
#### 12. Draw a magenta rectangle that encompasses the eagle.
```
img = cv2.imread("eagle.png.jpeg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

rcol = (255, 0, 255)

# Correct rectangle around eagle
cv2.rectangle(img_rgb, (200, 30), (550, 450), rcol, 4)
```

#### 13. Display the final annotated image.
```
plt.figure(figsize=(8,6))
plt.imshow(img_rgb)
plt.title("Annotated Image")
plt.axis("on")
plt.show()
```

#### 14. Read the image ('Eagle.jpg').
```
img = cv2.imread("eagle.png.jpeg", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

```
#### 15. Adjust the brightness of the image.
```
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```
img_brighter = cv2.add(img_rgb, m)
img_darker = cv2.subtract(img_rgb, m)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(img_darker)
plt.title("Darker Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(img_brighter)
plt.title("Brighter Image")
plt.axis("off")

plt.show()

```

#### 18. Modify the image contrast.
```
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2

# Apply contrast
img_higher1 = cv2.multiply(img_rgb.astype("float32"), matrix1)
img_higher2 = cv2.multiply(img_rgb.astype("float32"), matrix2)

# Convert back to uint8
img_higher1 = np.clip(img_higher1, 0, 255).astype("uint8")
img_higher2 = np.clip(img_higher2, 0, 255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(img_higher1)
plt.title("Higher Contrast (1.1x)")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(img_higher2)
plt.title("Higher Contrast (1.2x)")
plt.axis("off")

plt.show()
```

#### 20. Split the image (eagle.jpg) into the B,G,R components & Display the channels.
```
b, g, r = cv2.split(img)

plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(b, cmap='gray')
plt.title("Blue Channel")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(g, cmap='gray')
plt.title("Green Channel")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(r, cmap='gray')
plt.title("Red Channel")
plt.axis("off")

plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```
merged_rgb = cv2.merge([r, g, b])

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```
hsv_img = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)

plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(h, cmap='gray')
plt.title("Hue Channel")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(s, cmap='gray')
plt.title("Saturation Channel")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(v, cmap='gray')
plt.title("Value Channel")
plt.axis("off")

plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.merge([h, s, v])
merged_rgb_from_hsv = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB)

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(merged_rgb_from_hsv)
plt.title("Merged HSV Image")
plt.axis("off")

plt.show()
```

## Output:
- **i)**  <img width="608" height="472" alt="image" src="https://github.com/user-attachments/assets/5241d945-72ce-4cb0-935d-385e96d49466" />

- **ii)** <img width="623" height="479" alt="image" src="https://github.com/user-attachments/assets/c12cf44c-9369-4fb5-92cf-66fd7d41f98e" />

- **iii)** <img width="544" height="479" alt="image" src="https://github.com/user-attachments/assets/3a22bdda-bce8-42ac-93ec-f9a8030ca842" />
  
- **iv)** <img width="474" height="473" alt="image" src="https://github.com/user-attachments/assets/4c58a63e-7169-4d82-a045-a95aa76f7ab0" />

- **v)**   <img width="611" height="499" alt="image" src="https://github.com/user-attachments/assets/6ae08455-5866-4858-9d34-fb6391cd0c2e" />

- **vi)** <img width="611" height="410" alt="image" src="https://github.com/user-attachments/assets/85cad514-129d-4208-a4a2-569ed53a9df7" />

-**vii)** <img width="661" height="192" alt="image" src="https://github.com/user-attachments/assets/28cfcec8-d268-42e5-bfb2-09763e2700b0" />

-**viii)** <img width="681" height="178" alt="image" src="https://github.com/user-attachments/assets/91a5e543-5a3c-4889-adbb-6ba76a91b7bb" />

-**xi)** <img width="672" height="190" alt="image" src="https://github.com/user-attachments/assets/31587103-021a-4497-a36a-ef5bcc9807e7" />

-**x)** <img width="678" height="274" alt="image" src="https://github.com/user-attachments/assets/22fe8238-e975-4292-92be-67bb44f2fe0b" />

-**xi)** <img width="679" height="174" alt="image" src="https://github.com/user-attachments/assets/bd0be009-1338-423b-8211-d4dbdfc0fbc2" />

-**xii)** <img width="688" height="271" alt="image" src="https://github.com/user-attachments/assets/b5dd0a36-9505-40e9-9956-1f6ddd9e2b04" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

