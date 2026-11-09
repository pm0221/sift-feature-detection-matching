# SIFT (Scale-Invariant Feature Transform) Feature Detection and Matching

## Project Overview
This project demonstrates feature detection and feature matching between two versions of an image using the Scale-Invariant Feature Transform (SIFT) algorithm in OpenCV.

A training image is loaded, and a test image is created by reducing its size and rotating it by 30 degrees. SIFT is then used to detect keypoints and calculate descriptors in both images. A Brute Force Matcher matches the descriptors, and the matching points are visualized.

The implementation is provided in the Jupyter Notebook `CV2_SIFT.ipynb`.

## Objectives
- Load and display a training image.
- Generate a test image with scale and rotation changes.
- Convert images to grayscale for feature extraction.
- Detect SIFT keypoints.
- Calculate SIFT descriptors.
- Display keypoints with and without their scale information.
- Match descriptors using a Brute Force Matcher.
- Visualize the best matching points and count the matches.

## Image Input
The notebook expects the input image at:

```text
/content/cute-elephant-playing-ball-circus-cartoon-vector-icon-illustration-animal-sport-icon-isolated-flat_138676-7809.avif
```

Place the image at this path when using Google Colab, or update the `cv2.imread()` path to the location of your image in your environment.

## Project Workflow

### 1. Import Libraries
The notebook uses:
- **OpenCV (`cv2`)** – image processing, SIFT feature extraction, and descriptor matching.
- **NumPy** – image array operations.
- **Matplotlib** – displaying images and visual results.

### 2. Load and Prepare Images
- Read the input image using OpenCV.
- Convert the image from BGR to RGB for display.
- Convert the training image to grayscale.
- Create a smaller test image using two successive `cv2.pyrDown()` operations.
- Rotate the test image by 30 degrees using `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`.
- Convert the test image to grayscale.
- Display the original training image and transformed test image side by side.

### 3. Detect Keypoints and Create Descriptors
Create a SIFT detector using:

```python
sift = cv2.SIFT_create()
```

Use `detectAndCompute()` on the grayscale training and test images to:
- Detect distinctive keypoints.
- Calculate a descriptor for each detected keypoint.

The notebook displays the training image keypoints in two ways:
- **Without size:** Shows keypoint locations.
- **With size:** Shows keypoint locations and their scale/orientation information.

It also prints the number of keypoints detected in the training and test images.

### 4. Match Keypoints
The notebook creates a Brute Force Matcher using the L1 distance norm:

```python
bf = cv2.BFMatcher(cv2.NORM_L1, crossCheck=False)
```

It then:
- Matches the training descriptors with the test descriptors.
- Sorts matches by distance, with shorter distances appearing first.
- Draws the matching points using `cv2.drawMatches()`.
- Displays the combined matching visualization.
- Prints the total number of matches.

The notebook contains two matching code cells that perform this matching and visualization.

## Technologies and Libraries
- Python
- OpenCV
- NumPy
- Matplotlib
- Jupyter Notebook

## Installation

Install the required packages:

```bash
pip install opencv-contrib-python numpy matplotlib jupyter
```

SIFT is available in current OpenCV builds. If your environment already has a compatible OpenCV installation with SIFT support, you may not need to install `opencv-contrib-python` separately.

## How to Run
1. Open the notebook in Jupyter Notebook, JupyterLab, or Google Colab.
2. Install the required libraries.
3. Make the input AVIF image available at the path specified in the notebook, or update the image path.
4. Run the image-loading and transformation cell.
5. Run the keypoint detection and descriptor creation cell.
6. Run either of the matching cells to visualize and count the matches.

**Important execution order:** In the notebook as currently arranged, the first matching cell appears before the cell that creates `train_descriptor` and `test_descriptor`. Run the keypoint/descriptor cell first, then run the matching cell; otherwise, the descriptors will not yet be defined.

## Project Structure

```text
SIFT_Feature_Detection/
├── CV2_SIFT.ipynb
├── README.md
└── cute-elephant-playing-ball-circus-cartoon-vector-icon-illustration-animal-sport-icon-isolated-flat_138676-7809.avif
```

## Notes
- The test image is created by downscaling the training image twice and rotating it by 30 degrees.
- Matching quality depends on the image content and the detected descriptors.
- The notebook displays results and prints keypoint and match counts; it does not save the visualizations as separate image files by default.
- AVIF image support depends on the OpenCV build and environment. If the image cannot be loaded, use a supported image format such as PNG or JPEG and update the file path.

## Author
Prayag Maru
