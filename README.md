# Workshop--1-Adding-Sunglasses-to-Your-Passport-Photo-Using-OpenCV
## Aim

To develop an image processing application using Python and OpenCV that adds sunglasses to a face image by overlaying a transparent sunglass image onto the eye region.

---

## Software Required

* Python 3.x
* OpenCV (`cv2`)
* NumPy
* Matplotlib
* Jupyter Notebook / Google Colab

---

## Algorithm

1. Import the required libraries such as OpenCV, NumPy, and Matplotlib.
2. Load the face image.
3. Load the sunglass PNG image with an alpha (transparent) channel.
4. Resize the sunglass image to fit the face image properly.
5. Separate the RGB and alpha channels of the sunglass image.
6. Select the Region of Interest (ROI) on the face where the sunglasses should be placed.
7. Resize the sunglass image according to the ROI size.
8. Blend the sunglass image with the face image using masking and alpha blending techniques.
9. Display the final output image with sunglasses.

---

## Program:

```py

import cv2
import numpy as np
import matplotlib.pyplot as plt

faceImage = cv2.imread('img.png')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")

faceImage.shape

glassPNG = cv2.imread('glass.png',-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")

glassPNG = cv2.resize(glassPNG,(460,170))
print("image Dimension ={}".format(glassPNG.shape))

glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]

plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');

y1, y2 = 300, 470
x1, x2 = 290, 750

roi = faceWithGlassesNaive[y1:y2, x1:x2]
resized = cv2.resize(glassBGR, (roi.shape[1], roi.shape[0]))
faceWithGlassesNaive[y1:y2, x1:x2] = resized

import cv2

faceImage = cv2.imread("img.png")


if faceImage is None:
    print("Image not found. Make sure 'kritika.jpg' is in the same folder as this notebook.")
else:
    faceWithGlassesArithmetic = faceImage.copy()
    print("Image loaded successfully!")import cv2

faceImage = cv2.imread("img.png")

if faceImage is None:
    print("Image not found. Make sure 'kritika.jpg' is in the same folder as this notebook.")
else:
    faceWithGlassesArithmetic = faceImage.copy()
    print("Image loaded successfully!")

import cv2

faceImage = cv2.imread("img.png")
glass = cv2.imread("glass.png")

faceWithGlassesArithmetic = faceImage.copy()

y1, y2 = 300, 470
x1, x2 = 290, 750

roi = faceWithGlassesArithmetic[y1:y2, x1:x2]

glass_resized = cv2.resize(glass, (roi.shape[1], roi.shape[0]))

faceWithGlassesArithmetic[y1:y2, x1:x2] = glass_resized

import cv2
import matplotlib.pyplot as plt

# Read images
face = cv2.imread("img.png")
glass = cv2.imread("glass.png", cv2.IMREAD_UNCHANGED)

glass = cv2.resize(glass, (220, 90))

x = 105
y = 120

h, w = glass.shape[:2]

glass_rgb = glass[:, :, :3]
alpha = glass[:, :, 3] / 255.0

for c in range(3):
    face[y:y+h, x:x+w, c] = (
        alpha * glass_rgb[:, :, c] +
        (1 - alpha) * face[y:y+h, x:x+w, c]
    )

result = cv2.cvtColor(face, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(6,8))
plt.imshow(result)
plt.axis("off")
plt.title("Sunglasses Fitted")
plt.show()

# Save output
cv2.imwrite("final_output.png", face)

print("Sunglasses fitted successfully")

```

## Output:

![alt text](image.png)

![alt text](image-1.png)

## Result

The program successfully detects the selected face region and overlays the sunglass image onto the face, producing a realistic image of a person wearing sunglasses using image processing techniques in OpenCV.