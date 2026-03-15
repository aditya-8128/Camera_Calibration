Markdown
# Camera Calibration using OpenCV (Zhang's Method)

This repository contains a robust Python implementation of a camera calibration module using OpenCV. The software utilizes Zhang's Method to extract the 5 intrinsic parameters, 6 extrinsic parameters, and lens distortion coefficients from a set of stereocamera checkerboard images. 

This project was completed as a course assignment for the School of Electrical and Computer Sciences at IIT Bhubaneswar.

## Features
* **Dynamic Grid Auto-Detection:** Automatically scans and tests multiple candidate grid sizes (e.g., 6x5, 11x8) using various image processing techniques (histogram equalization, multi-scale resizing) to maximize successful detections across imperfect datasets.
* **Sub-Pixel Corner Refinement:** Utilizes `cv2.cornerSubPix` to refine detected corners to fractional pixel accuracy, drastically lowering reprojection error.
* **Comprehensive Metrics:** Calculates and outputs both the overall Root Mean Square (RMS) error and the average per-image Mean Reprojection Error.
* **Auto-Undistortion:** Automatically generates and saves an undistorted sample image based on the calculated camera matrix.


## Prerequisites
Ensure you have Python 3.x installed along with the following standard computer vision libraries:

Bash
pip install opencv-python numpy matplotlib

How to Execute the Code
You can run this code either locally on your machine or in a cloud notebook environment (like Kaggle or Google Colab).

Option A: Running Locally (Terminal / Command Prompt)
Extract the submission ZIP file to a local directory.

Open the full_camera_calibration_auto_detect.py file in any text editor or IDE.

Locate the USER CONFIGURATION section at the very top of the script.

Update the image_path_glob variable to point to the included sample images folder. For example:

Python
image_path_glob = './data/leftcamera/*.png'
Open your terminal, navigate to the extracted folder, and execute the script:

Bash
python full_camera_calibration_auto_detect.py
Option B: Running in Kaggle / Google Colab
Upload the full_camera_calibration_auto_detect.py script content into a new notebook cell.

Upload the sample images folder to the working directory or dataset input folder.

Update the image_path_glob variable to match the cloud path. For example, in Kaggle:

Python
image_path_glob = '/kaggle/input/your-dataset-name/data/imgs/leftcamera/*.png'
Run the cell. Matplotlib will automatically display the corner detection visualizations inline.

## Expected Output
Upon successful execution, the script will output the following directly to the console/terminal:

The optimal inner-corner grid size automatically selected by the algorithm.

The mathematically extracted 3x3 Intrinsic Camera Matrix (K).

Extracted Focal Lengths (fx, fy), Principal Points (cx, cy), and Skew (gamma).

Lens Distortion Coefficients (k1, k2, p1, p2, k3).

The Extrinsic Parameters (Rotation and Translation vectors).

The Overall RMS Error and Mean Reprojection Error to validate accuracy.

Generated Artifacts:
The script will automatically create a directory (default: /calib_auto/) and save the following files:

camera_calib.npz: A NumPy archive containing all the calculated matrices and vectors for future use.

first_detection_[WxH].png: A visual confirmation image showing the drawn checkerboard corners.

undistorted_example.png: An example of an image from the dataset with the calculated lens distortion mathematically removed.

