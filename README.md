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
- **Name:** [Your Name Here]  
- **Register Number:** [Your Register Number Here]

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
# YOUR CODE HERE
img_gray = cv2.imread(r"C:\Users\acer\Desktop\eagle.jpg", cv2.IMREAD_GRAYSCALE)

```

#### 2. Print the image width, height & Channel.
```python
print("Width:", img_gray.shape[1], "Height:", img_gray.shape[0], "Channels:", 1)

```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img_gray, cmap='gray')
plt.title("Grayscale Eagle")
plt.axis("off")
plt.show()

```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite("Eagle_in_Flight.png", img_gray)

```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img_color = cv2.imread("Eagle_in_Flight.png")

```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
print("Width:", img_color.shape[1], "Height:", img_color.shape[0], "Channels:", img_color.shape[2])
plt.imshow(cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB))
plt.title("Color Eagle")
plt.axis("off")
plt.show()

```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
crop_eagle = img_color[50:300, 100:400]

```

#### 8. Resize the image up by a factor of 2x.
```python
resized_eagle = cv2.resize(crop_eagle, None, fx=2, fy=2)

```

#### 9. Flip the cropped/resized image horizontally.
```python
flipped_eagle = cv2.flip(resized_eagle, 1)
plt.imshow(cv2.cvtColor(flipped_eagle, cv2.COLOR_BGR2RGB))
plt.title("Cropped, Resized, Flipped Eagle")
plt.axis("off")
plt.show()

```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
apollo = cv2.imread(r"C:\Users\acer\Desktop\appolo11launch.jpg")

```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
cv2.putText(apollo, text, (50, apollo.shape[0]-30), font_face, 1.5, (255,255,255), 2)

```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rect_color = magenta
cv2.rectangle(apollo, (250,50), (450,600), (255,0,255), 3)

```

#### 13. Display the final annotated image.
```python
plt.imshow(cv2.cvtColor(apollo, cv2.COLOR_BGR2RGB))
plt.title("Annotated Apollo 11 Launch")
plt.axis("off")
plt.show()

```

#### 14. Read the image ('Boy.jpg').
```python
boy = cv2.imread(r"C:\Users\acer\Desktop\Edwin-Aldrin-Moon-July-20-1969.webp")

```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)
# matrix_ones = 
matrix_ones = np.ones(boy.shape, dtype="uint8") * 50

```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
img_brighter = cv2.add(boy, matrix_ones)
img_darker = cv2.subtract(boy, matrix_ones)

```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(12,4))
for i, im in enumerate([boy, img_darker, img_brighter]):
    plt.subplot(1,3,i+1)
    plt.imshow(cv2.cvtColor(im, cv2.COLOR_BGR2RGB))
    plt.title(["Original","Darker","Brighter"][i])
    plt.axis("off")
plt.show()

```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
matrix1 = 
matrix2 = 
# img_higher1 = 
# img_higher2 = 
img_higher1 = cv2.convertScaleAbs(boy, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(boy, alpha=1.2, beta=0)

```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(12,4))
for i, im in enumerate([boy, img_higher1, img_higher2]):
    plt.subplot(1,3,i+1)
    plt.imshow(cv2.cvtColor(im, cv2.COLOR_BGR2RGB))
    plt.title(["Original","Contrast 1.1","Contrast 1.2"][i])
    plt.axis("off")
plt.show()

```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b,g,r = cv2.split(boy)
plt.figure(figsize=(12,4))
for i, im in enumerate([b,g,r]):
    plt.subplot(1,3,i+1)
    plt.imshow(im, cmap='gray')
    plt.title(["Blue","Green","Red"][i])
    plt.axis("off")
plt.show()

```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_bgr = cv2.merge([b,g,r])
plt.imshow(cv2.cvtColor(merged_bgr, cv2.COLOR_BGR2RGB))
plt.title("Merged BGR")
plt.axis("off")
plt.show()

```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv = cv2.cvtColor(boy, cv2.COLOR_BGR2HSV)
h,s,v = cv2.split(hsv)
plt.figure(figsize=(12,4))
for i, im in enumerate([h,s,v]):
    plt.subplot(1,3,i+1)
    plt.imshow(im, cmap='gray')
    plt.title(["Hue","Saturation","Value"][i])
    plt.axis("off")
plt.show()

```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.merge([h,s,v])
plt.imshow(cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB))
plt.title("Merged HSV")
plt.axis("off")
plt.show()

```

## Output:
- **i)** Read and Display an Image.

 <img width="462" height="505" alt="Screenshot 2026-08-18 110803" src="https://github.com/user-attachments/assets/0fe81d81-99de-438e-97a8-ff99bd3176b1" />
 
- **ii)** Adjust Image Brightness.
 <img width="521" height="141" alt="Screenshot 2026-08-18 110835" src="https://github.com/user-attachments/assets/0cbe317e-3c56-4a3a-80d7-1c5f8a15f2bb" />

  **iii)** Modify Image Contrast.

<img width="515" height="143" alt="Screenshot 2026-08-18 110843" src="https://github.com/user-attachments/assets/299b93b9-0f1f-4287-b1d8-a4b0d75b139f" />

- **iv)** Generate Third Image Using Bitwise Operations.

  <img width="500" height="409" alt="Screenshot 2026-08-18 110859" src="https://github.com/user-attachments/assets/3b1a36d8-50f8-4150-8fe9-7f9055f0c80b" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

