# Computer Vision Project
### Image Processing, Restoration, Feature Extraction, and Feature Matching

## 1. Project Overview

This project explores how computers can process images, improve image quality, identify important visual details, and find similarities between different photographs.

Computer vision is a field of artificial intelligence that enables computers to extract useful information from images and videos. It is used in applications such as medical imaging, facial recognition, industrial quality inspection, autonomous vehicles, and security systems.

This project uses Python-based computer vision techniques to investigate image processing and visual feature analysis through practical experiments.

The work documented here covers two tasks:

- **Task 1: Image Processing, Restoration, and Segmentation**
- **Task 2: Feature Extraction and Feature Matching**

Each task is implemented in a Jupyter Notebook, with code, visualizations, and saved results to support understanding and evaluation.

## 2. Project Objectives

The main objectives are to:

- Understand how computers represent and process digital images.
- Investigate how noise affects image quality.
- Apply filtering techniques to reduce unwanted noise.
- Evaluate processed images using numerical image quality metrics.
- Explore methods for separating image regions and identifying boundaries.
- Extract meaningful visual features from photographs.
- Detect distinctive points and match them across two images.
- Study how rotation and resizing affect feature detection and matching.
- Develop practical experience with Python and computer vision libraries.

## 3. Technologies and Tools

| Technology | Purpose |
|---|---|
| Python | Programming language used to implement the experiments. |
| OpenCV | Image processing, filtering, feature detection, and feature matching. |
| NumPy | Numerical calculations and storage of image feature data. |
| Matplotlib | Displaying images and visualizing results. |
| scikit-image | Supporting image processing and image quality evaluation. |
| Jupyter Notebook | Running code step by step and displaying results alongside explanations. |
| Visual Studio Code | Development environment used to create and run the notebooks. |
| Git and GitHub | Version control and online hosting of the project. |

---

# Task 1: Image Processing, Restoration, and Segmentation

## 4. Introduction

Images captured by cameras or other devices may contain unwanted noise, unclear boundaries, or regions that are difficult to distinguish. Image processing provides methods to improve image appearance and make important structures easier to analyze.

In this task, an original photograph is used to explore noise generation, image filtering, quality evaluation, segmentation, morphological operations, edge detection, and watershed segmentation.

**Notebook:** `notebooks/Task1_Image_Processing.ipynb`

## 4.1 Image Loading and Grayscale Conversion

The original photograph is loaded into Python and displayed for inspection. A grayscale version is also created.

A grayscale image represents brightness using shades ranging from black to white instead of separate red, green, and blue colour channels.

**Why it matters:** Many image processing algorithms work directly with brightness information. Grayscale conversion simplifies these operations and provides a useful starting point for thresholding and edge detection.

**Output:** `outputs/grayscale.png`

## 4.2 Noise Generation

Noise is unwanted variation in image pixels. It can make an image appear grainy or introduce spots that obscure important details.

Two types of artificial noise were generated to study their effects.

### Gaussian Noise

Gaussian noise adds random variations to pixel intensities. It can resemble grain or random interference in a photograph.

### Salt-and-Pepper Noise

Salt-and-pepper noise introduces isolated bright and dark pixels, making the image appear as though small white and black spots have been scattered across it.

These experiments provide noisy versions of the original photograph for comparison with the filtered results.

**Outputs:**

- `outputs/gaussian_noise.png`
- `outputs/salt_pepper_noise.png`

## 4.3 Image Restoration and Filtering

Image restoration attempts to reduce unwanted noise while preserving useful visual information.

Two filtering methods were applied.

### Gaussian Blur

Gaussian Blur smooths an image by combining nearby pixel values using weighted averaging. It can reduce gradual random noise, although it may also soften fine details.

### Median Filtering

Median filtering replaces a pixel value with the median of values in its neighbourhood. It is particularly effective for removing isolated bright and dark spots, such as salt-and-pepper noise.

Comparing the two methods helps demonstrate that different types of noise may respond better to different filters.

**Outputs:**

- `outputs/gaussian_filtered.png`
- `outputs/median_filtered.png`

## 4.4 Image Quality Evaluation: PSNR and SSIM

Visual comparisons help us understand how an image changes, but numerical metrics provide additional information about image quality.

Two metrics were calculated by comparing processed images with the original photograph.

### Peak Signal-to-Noise Ratio (PSNR)

PSNR measures the difference between an original image and a processed image using a logarithmic scale. A higher PSNR generally indicates lower pixel-level error.

### Structural Similarity Index (SSIM)

SSIM compares structural information, brightness, and contrast between two images. It helps assess whether the processed image retains visual characteristics similar to the original.

Both metrics were calculated during the restoration experiments, and the results were saved in a CSV file.

**Output:** `outputs/restoration_metrics.csv`

The actual metric values can be inspected in the CSV file. The interpretation depends on the measured results and the images being compared.

## 4.5 Image Thresholding and Segmentation

Image segmentation separates an image into regions. Thresholding is a basic segmentation technique that classifies pixels according to their brightness.

Three approaches were implemented.

### Global Thresholding

A single brightness threshold is applied to the entire image. Pixels are divided into groups according to whether their values fall above or below the selected threshold.

### Otsu's Thresholding

Otsu's method automatically selects a threshold based on the distribution of image brightness values. It can be useful when the foreground and background have distinguishable intensity distributions.

### Adaptive Thresholding

Adaptive thresholding calculates thresholds for local regions rather than using one value for the entire image. This can help when lighting varies across different parts of a photograph.

These techniques demonstrate different approaches to separating image regions based on brightness.

## 4.6 Morphological Operations

Morphological operations modify the shapes of foreground regions in a binary image. They are often used to clean up the results of thresholding.

Four operations were implemented:

- **Erosion:** Shrinks foreground regions and can remove small isolated details.
- **Dilation:** Expands foreground regions and can help connect nearby areas.
- **Opening:** Applies erosion followed by dilation to help remove small foreground noise.
- **Closing:** Applies dilation followed by erosion to help fill small gaps and holes.

These operations demonstrate how binary images can be refined before further analysis.

## 4.7 Edge Detection Using Canny

Edges are locations where image intensity changes significantly. They may correspond to object outlines, lines, or transitions between regions.

The Canny edge detector was applied to identify prominent boundaries in the photograph.

The resulting image emphasizes edges rather than showing all the original colour and texture information.

**Why it matters:** Edge detection is useful in shape analysis, boundary identification, object detection, and other computer vision applications.

## 4.8 Watershed Segmentation

Watershed segmentation is a method for dividing an image into regions. It can be useful when attempting to separate objects that touch or overlap.

The method uses image information and markers to guide the segmentation process. The resulting visualization highlights estimated region boundaries.

The quality of the segmentation depends on the input image and the markers used by the algorithm.

## 4.9 Task 1 Summary

Task 1 demonstrates how image processing techniques can improve image appearance and reveal useful structures.

The experiments cover:

- Converting colour images to grayscale.
- Generating Gaussian and salt-and-pepper noise.
- Applying Gaussian and median filters.
- Measuring image quality using PSNR and SSIM.
- Segmenting images using global, Otsu's, and adaptive thresholding.
- Refining binary images using morphological operations.
- Detecting boundaries with Canny edge detection.
- Exploring region separation using watershed segmentation.

Together, these experiments provide a practical introduction to image enhancement, image analysis, and segmentation.

---

# Task 2: Feature Extraction and Feature Matching

## 5. Introduction

An image contains more than colours and brightness. It also contains distinctive visual details such as corners, edges, textures, and patterns.

Feature extraction identifies useful information from an image. Feature matching compares this information across images to find corresponding visual details.

For example, two photographs may show the same object from different angles or at different sizes. Feature matching attempts to identify points that represent similar parts of that object in both photographs.

**Notebook:** `notebooks/Task2_Feature_Matching.ipynb`

## 5.1 Loading and Preparing Images

Two images are loaded and displayed for comparison. Their dimensions are inspected, and grayscale versions are prepared for feature extraction.

To keep SIFT processing manageable, the images are resized when necessary before keypoint detection.

**Input images:**

- `input/original.jpg`
- `input/second.jpg`

For meaningful comparisons, the images should ideally contain the same object or scene under different viewing conditions.

## 5.2 HOG Feature Extraction

Histogram of Oriented Gradients (HOG) is a technique for describing the shapes and local edge patterns in an image.

Rather than relying only on individual pixel values, HOG examines the directions of brightness changes in small image regions and summarizes those patterns into numerical features.

These features can help represent the shape and structure of objects.

**Why it matters:** HOG provides a structured numerical description of visual patterns. It has been used in applications such as object detection and pedestrian recognition.

HOG features were calculated for both input images and saved as NumPy arrays.

**Outputs:**

- `outputs/hog_features_1.npy`
- `outputs/hog_features_2.npy`

These files contain numerical feature data that can be loaded for further analysis.

## 5.3 SIFT Keypoint Detection

Scale-Invariant Feature Transform (SIFT) is a method for finding distinctive points in images. It is designed to be relatively robust to rotation and changes in image scale.

These distinctive points are called **keypoints**. They may occur around corners, textured areas, and other visually informative locations.

SIFT also calculates a descriptor for each keypoint. A descriptor is a numerical representation of the local visual pattern around that point.

The notebook detects SIFT keypoints in both images and displays them to show where distinctive features were found.

**Outputs:**

- `outputs/sift_keypoints_1.png`
- `outputs/sift_keypoints_2.png`

The corresponding descriptor arrays are saved when available:

- `outputs/sift_descriptors_1.npy`
- `outputs/sift_descriptors_2.npy`

## 5.4 SIFT Feature Matching

After extracting descriptors, the next step is to compare them across the two images.

A Brute-Force Matcher compares descriptors to identify similar candidates. Lowe's ratio test then filters some ambiguous matches by comparing the closest candidate with the second-closest candidate.

The remaining matches are visualized by drawing lines between corresponding keypoints in the two images.

**Observed result:** The matching experiment reported **510 good SIFT matches** for the selected input images and matching settings.

This number represents matches that passed the chosen filtering rule. It does not guarantee that every match is correct, so the visualization should also be inspected to check whether the lines connect corresponding visual details.

**Output:** `outputs/sift_matches.png`

## 5.5 Rotation Experiment

A copy of the first image was rotated by 45 degrees. SIFT keypoints and descriptors were then calculated for the rotated image.

The original image was compared with the rotated version to investigate whether distinctive visual features could still be detected and matched after a change in orientation.

SIFT is designed to be relatively robust to rotation, although the number and location of detected features may change.

**Outputs:**

- `outputs/rotated_image.png`
- `outputs/sift_rotated_matches.png`

The matching visualization shows the correspondences identified between the original and rotated images.

## 5.6 Resizing Experiment

The first image was also resized to 70% of its original dimensions.

SIFT was applied to the resized image, and its descriptors were matched against those extracted from the original image.

This experiment investigates how feature detection and matching behave when visual content appears at a different scale.

SIFT is designed to handle scale changes, but the exact keypoints and number of matches can still vary.

**Outputs:**

- `outputs/resized_image.png`
- `outputs/sift_resized_matches.png`

## 5.7 Task 2 Summary

Task 2 demonstrates how computers can extract and compare visual information across images.

The experiments cover:

- HOG feature extraction for describing image structure.
- SIFT keypoint detection for finding distinctive visual points.
- SIFT descriptors for numerically representing local image appearance.
- Feature matching using a Brute-Force Matcher.
- Filtering ambiguous matches using Lowe's ratio test.
- Visualizing matching points across two images.
- Testing feature detection and matching after rotation and resizing.

These techniques provide a foundation for applications such as image alignment, visual search, object recognition, and image registration.

---

## 6. Project Structure

The project is organized into separate folders for input images, generated results, notebooks, and supporting files.

```text
Computer Vision Project/
│
├── input/
│   ├── original.jpg
│   └── second.jpg
│
├── outputs/
│   ├── grayscale.png
│   ├── gaussian_noise.png
│   ├── salt_pepper_noise.png
│   ├── gaussian_filtered.png
│   ├── median_filtered.png
│   ├── restoration_metrics.csv
│   ├── sift_keypoints_1.png
│   ├── sift_keypoints_2.png
│   ├── sift_matches.png
│   ├── sift_rotated_matches.png
│   ├── sift_resized_matches.png
│   └── Additional generated results
│
├── notebooks/
│   ├── Task1_Image_Processing.ipynb
│   └── Task2_Feature_Matching.ipynb
│
├── report/
├── src/
├── requirements.txt
├── .gitignore
└── README.md
```

The listing illustrates the intended organization. The actual files in each folder may differ depending on which notebook cells have been executed and saved.

The local `venv` folder contains the Python virtual environment and is excluded from Git tracking.

## 7. How to Run the Project

### Prerequisites

- Python installed on your computer.
- Visual Studio Code with Jupyter Notebook support, or another compatible Jupyter environment.
- The Python packages listed in `requirements.txt`.

### Step 1: Obtain the project

Clone the GitHub repository using its actual URL:

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd Computer-Vision-Project
```

Alternatively, download the repository as a ZIP file from GitHub and extract it.

### Step 2: Create a virtual environment

On Windows, open a terminal in the project folder and run:

```powershell
python -m venv venv
```

Activate the environment in PowerShell:

```powershell
.\venv\Scripts\Activate.ps1
```

### Step 3: Install the required packages

Run:

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Step 4: Open the notebooks

Open the project folder in Visual Studio Code.

Navigate to the `notebooks` folder and open:

- `Task1_Image_Processing.ipynb`
- `Task2_Feature_Matching.ipynb`

Select the Python interpreter associated with the project's virtual environment and run the cells in order.

### Step 5: Inspect the results

Check that the required input images are available in `input/`.

Generated images, numerical feature arrays, and evaluation results are saved to `outputs/`.

The exact visual and numerical results may vary depending on the input photographs and processing settings.

---

## 8. Conclusion

This project demonstrates practical applications of image processing and feature analysis using Python.

Task 1 explores how images can be filtered, evaluated, segmented, and analyzed to reveal useful structures. Task 2 explores how distinctive visual features can be extracted and matched across images, including experiments involving rotation and resizing.

The notebooks combine implementation with visualizations and saved outputs, making it possible to inspect how each technique behaves on real image data.

The overall aim is to develop a clear practical understanding of computer vision concepts through experimentation, observation, and evaluation.
