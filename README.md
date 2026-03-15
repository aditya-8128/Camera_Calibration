# Camera Calibration using OpenCV (Zhang's Method)

This repository contains a robust Python implementation of a camera calibration module using OpenCV. The software utilizes Zhang's Method to extract the 5 intrinsic parameters, 6 extrinsic parameters, and lens distortion coefficients from a set of stereocamera checkerboard images. 

This project was completed as a course assignment for the School of Electrical and Computer Sciences at IIT Bhubaneswar.

## Features
* **Dynamic Grid Auto-Detection:** Automatically scans and tests multiple candidate grid sizes (e.g., 6x5, 11x8) using various image processing techniques (histogram equalization, multi-scale resizing) to maximize successful detections across imperfect datasets.
* **Sub-Pixel Corner Refinement:** Utilizes `cv2.cornerSubPix` to refine detected corners to fractional pixel accuracy, drastically lowering reprojection error.
* **Comprehensive Metrics:** Calculates and outputs both the overall Root Mean Square (RMS) error and the average per-image Mean Reprojection Error.
* **Auto-Undistortion:** Automatically generates and saves an undistorted sample image based on the calculated camera matrix.

## Submission Directory Structure
If you are evaluating the `.zip` submission, the folder structure is as follows:
```text
/
├── full_camera_calibration_auto_detect.py  # Main source code
├── README.md                               # Execution instructions
├── Report.pdf                              # Mathematical theory and methodology
└── data/                                   # Sample calibration images
    └── leftcamera/
        ├── Im_L_1.png
        └── ...
## Prerequisites
Ensure you have Python 3.x installed along with the following standard computer vision libraries:
