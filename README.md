# Exp 8-Image Segmentation Using Thresholding Techniques in OpenCV

## Developed By

**Name:** Srinivas J

**Register No:** 212225230276

## Aim

To segment an image using Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding techniques using Python and OpenCV.

The program performs the following operations:

- Global Thresholding
- Adaptive Thresholding
- Otsu's Thresholding

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Load the input image using OpenCV.

### Step 3:

Convert the input image into grayscale format.

### Step 4: Global Thresholding

- Select a fixed threshold value.

### Step 5: Adaptive Thresholding

- Compute threshold values for small regions of the image.
- Apply Adaptive Mean Thresholding.
- Apply Adaptive Gaussian Thresholding.
- Display the segmented images.

### Step 6: Otsu's Thresholding

- Automatically determine the optimal threshold value.
- Apply Otsu's thresholding technique.
- Display the segmented image.

### Step 7:

Compare the results obtained from Global, Adaptive, and Otsu's thresholding methods.

## Program

```py
import cv2
import matplotlib.pyplot as plt

# Step 1: Load the image
img = cv2.imread("hockey.png")

if img is None:
    print("Error: Image not found. Check the file path.")
else:
    # Step 2: Convert BGR to RGB
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Step 3: Convert into Grayscale
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    # Step 4: Global Thresholding
    _, global_thresh = cv2.threshold(
        gray, 127, 255, cv2.THRESH_BINARY
    )

    # Step 5: Adaptive Mean Thresholding
    adaptive_mean = cv2.adaptiveThreshold(
        gray, 255,
        cv2.ADAPTIVE_THRESH_MEAN_C,
        cv2.THRESH_BINARY,
        11, 2
    )

    # Step 6: Adaptive Gaussian Thresholding
    adaptive_gaussian = cv2.adaptiveThreshold(
        gray, 255,
        cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
        cv2.THRESH_BINARY,
        11, 2
    )

    # Step 7: Otsu's Thresholding
    otsu_value, otsu_thresh = cv2.threshold(
        gray, 0, 255,
        cv2.THRESH_BINARY + cv2.THRESH_OTSU
    )

    # Step 8: Display all outputs
    titles = [
        "Original Image",
        "Grayscale Image",
        "Global Thresholding",
        "Adaptive Mean",
        "Adaptive Gaussian",
        "Otsu's Thresholding"
    ]

    images = [
        img_rgb,
        gray,
        global_thresh,
        adaptive_mean,
        adaptive_gaussian,
        otsu_thresh
    ]

    plt.figure(figsize=(12, 8))

    for i in range(6):
        plt.subplot(2, 3, i + 1)

        if i == 0:
            plt.imshow(images[i])
        else:
            plt.imshow(images[i], cmap="gray")

        plt.title(titles[i])
        plt.axis("off")

    plt.tight_layout()
    plt.show()

    print("Otsu Threshold Value:", otsu_value)
    print("Image Segmentation Completed Successfully!")
```

## Output

<img width="1189" height="743" alt="download" src="https://github.com/user-attachments/assets/614614e1-c977-47a8-881c-a1f17fb8e7cc" />

### Original Grayscale Image

- The grayscale version of the input image is displayed.
- Serves as the input for thresholding operations.

### Global Thresholding

- Original image is displayed.
- Thresholded image is displayed.
- A fixed threshold value is used for segmentation.
- Pixels are classified as foreground or background.

### Adaptive Thresholding

- Original image is displayed.
- Adaptive Mean Thresholded image is displayed.
- Adaptive Gaussian Thresholded image is displayed.
- Threshold values vary across different regions of the image.
- Suitable for images with uneven illumination.

### Otsu's Thresholding

- Original image is displayed.
- Otsu segmented image is displayed.
- Optimal threshold value is calculated automatically.
- Produces improved segmentation for bimodal histograms.


## Result

Thus, image segmentation is successfully performed using **Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding** techniques in OpenCV. 
