# Computer Vision Project

## Install Required Libraries

Activate your project's virtual environment, then run:

```bash
python -m pip install opencv-contrib-python numpy matplotlib scikit-image ultralytics ipykernel
```

## Overview

This project explores how computers can process images, improve image quality, identify important visual details, and find similarities between different photographs.

Computer vision is a field of artificial intelligence that enables computers to extract useful information from images and videos. It is used in applications such as medical imaging, facial recognition, industrial quality inspection, autonomous vehicles, and security systems.

This project uses Python-based computer vision techniques to investigate image processing and visual feature analysis through practical experiments.

## Objectives

- **Task 1:** Image processing, restoration, and segmentation.
- **Task 2:** Feature extraction and matching.
- **Task 3:** Object recognition using Haar Cascade and YOLO.
- **Task 4:** Video motion estimation using frame differencing, GMM background subtraction, and Lucas–Kanade optical flow.

## Technologies and Libraries

| Library or Tool | Purpose |
|---|---|
| Python | Main programming language |
| OpenCV | Image processing, feature detection, matching, face detection, video processing, and optical flow |
| NumPy | Numerical operations and image arrays |
| Matplotlib | Displaying images and visualizing results |
| scikit-image | Image quality metrics, including PSNR and SSIM |
| Ultralytics | Loading and running the pretrained YOLO model |
| IPykernel | Connecting the Python environment to Jupyter notebooks |
| Git and GitHub | Version control and project hosting |

## Project Structure

```text
Computer Vision Project/
├── input/                  # Input images and video
├── outputs/                # Generated results
├── report/                 # Project report
├── notebooks/
│   ├── Task1_Image_Processing.ipynb
│   ├── Task2_Feature_Matching.ipynb
│   ├── Task3_Object_Recognition.ipynb
│   └── Task4_Video_Motion.ipynb
├── models/                 # Supporting model files, if required
├── requirements.txt        # Python dependencies
├── README.md
└── .gitignore
```

## Task 1: Image Processing and Segmentation

### Aim

To investigate image restoration and segmentation techniques using digital images.

### Methods

- Adding Gaussian and salt-and-pepper noise.
- Applying Gaussian and median filters.
- Evaluating image restoration using Peak Signal-to-Noise Ratio (PSNR) and Structural Similarity Index Measure (SSIM).
- Applying global, Otsu, and adaptive thresholding.
- Performing erosion, dilation, opening, and closing.
- Detecting edges using Canny edge detection.
- Applying watershed segmentation.

### Example Outputs

- Noisy and filtered images.
- Thresholding and morphological results.
- Edge detection and watershed visualizations.
- `restoration_metrics.csv`

## Task 2: Feature Extraction and Matching

### Aim

To extract and match visual features between images and investigate how transformations affect matching.

### Methods

- Histogram of Oriented Gradients (HOG) feature extraction.
- Scale-Invariant Feature Transform (SIFT) keypoint and descriptor extraction.
- Brute-force feature matching.
- Lowe's ratio test to filter matches.
- Feature matching after image rotation and resizing.

### Example Outputs

- HOG feature arrays.
- SIFT keypoint visualizations and descriptor arrays.
- Feature matching visualizations.
- Rotated and resized image results.

## Task 3: Object Recognition

### Aim

To compare Haar Cascade face detection and YOLO object detection using a portrait image.

### Methods

**Haar Cascade**

Uses a pretrained cascade classifier to identify frontal faces. Detected regions are displayed using bounding boxes.

**YOLO**

Uses a pretrained deep learning model to detect and classify objects in an image. The results include bounding boxes, class labels, and confidence scores where available.

### Implementation

The same input portrait is processed using both methods. Their detection results are visualized and compared to examine their capabilities and limitations.

### Example Outputs

- `haar_cascade_result.jpg`
- `yolo_result.jpg`

### Notes

The Haar Cascade XML classifier must be available at the path specified in the notebook. YOLO may download its pretrained model weights on the first run, so an internet connection may be required.

## Task 4: Video Motion Estimation

### Aim

To explore different computer vision techniques for detecting and estimating motion in a video.

### Methods

**Frame Differencing**

Compares consecutive frames to identify pixel changes that may indicate movement.

**GMM Background Subtraction**

Uses OpenCV's MOG2 background subtraction method to separate foreground regions from a relatively stationary background.

**Lucas–Kanade Optical Flow**

Tracks feature points between consecutive frames to estimate their direction and approximate movement.

### Implementation

A self-recorded video is processed using all three techniques. The generated visualizations are compared to understand how each method identifies motion and how lighting, background changes, and camera movement can affect the results.

### Example Outputs

- `frame_difference.png`
- `frame_difference_mask.png`
- `gmm_background_subtraction.mp4`
- `gmm_foreground_mask.png`
- `lucas_kanade_optical_flow.png`

Some outputs depend on video length and whether sufficient feature points or frames are available.

## Installation and Setup

### Prerequisites

Install the following:

- Python 3.10 or 3.11 recommended.
- Visual Studio Code.
- Python and Jupyter extensions for VS Code.
- Git, if you want to clone or update the repository.

Official download pages:

- Python: https://www.python.org/downloads/
- VS Code: https://code.visualstudio.com/
- Git: https://git-scm.com/downloads/

### 1. Open the Project

Open the project folder in VS Code.

If cloning the repository for the first time, run:

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd Computer-Vision-Project
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with the URL of your GitHub repository.

### 2. Create a Virtual Environment

On Windows, open the VS Code terminal in the project folder:

```powershell
python -m venv venv
```

Activate the environment in PowerShell:

```powershell
.\venv\Scripts\Activate.ps1
```

If you are using Command Prompt instead, run:

```bat
venv\Scripts\activate.bat
```

### 3. Install the Libraries

Run:

```bash
python -m pip install --upgrade pip
python -m pip install opencv-contrib-python numpy matplotlib scikit-image ultralytics ipykernel
```

Use `opencv-contrib-python` for the OpenCV functionality required by the project, including SIFT support. Avoid installing multiple OpenCV wheel packages in the same environment.

### 4. Register the Jupyter Kernel

Run:

```bash
python -m ipykernel install --user --name cv-project --display-name "Python (Computer Vision Project)"
```

In VS Code, open a notebook and select **Python (Computer Vision Project)** from the kernel selector.

## Input Files

Place the required input files in the `input/` directory.

| Task | Required Input |
|---|---|
| Task 1 | `original.jpg` |
| Task 2 | `original.jpg` and `second.jpg` |
| Task 3 | `portrait.jpg` |
| Task 4 | `motion_video.mp4` |

Use your own photographs and recorded video where required. The filenames and paths in the notebooks must match the files in the input folder.

Avoid publishing personal photographs or videos to a public repository unless you intend to share them.

## How to Run the Notebooks

1. Open the project folder in VS Code.
2. Activate the virtual environment.
3. Install the required libraries.
4. Open the notebook for the task you want to run.
5. Select the **Python (Computer Vision Project)** kernel.
6. Run the notebook cells from top to bottom.
7. Review the visualizations and results.
8. Check the `outputs/` directory for generated files.

Run the notebooks in this order:

1. `Task1_Image_Processing.ipynb`
2. `Task2_Feature_Matching.ipynb`
3. `Task3_Object_Recognition.ipynb`
4. `Task4_Video_Motion.ipynb`

## Troubleshooting

**Input image or video not found**

Check that the file exists in `input/` and that the path and filename in the notebook are correct.

**A Python library cannot be imported**

Activate the correct virtual environment and install the required libraries again.

**The wrong notebook kernel is selected**

Select **Python (Computer Vision Project)** and restart the kernel.

**The Haar Cascade model cannot be loaded**

Check that the XML classifier exists at the specified path and can be loaded by OpenCV.

**YOLO cannot download model weights**

Check the internet connection and rerun the model-loading cell.

**Some output files are missing**

Check that the corresponding notebook cells ran successfully. Certain results depend on the length and content of the input video.

## Conclusion

This project demonstrates practical computer vision techniques for image restoration, segmentation, feature extraction, feature matching, object recognition, and video motion estimation. The experiments and visual outputs help illustrate the strengths and limitations of the different approaches.
