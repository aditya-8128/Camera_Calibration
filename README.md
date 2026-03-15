Markdown
# Camera Calibration using OpenCV (Zhang's Method)

This repository contains a robust Python implementation of a camera calibration module using OpenCV. The software utilizes Zhang's Method to extract the 5 intrinsic parameters, 6 extrinsic parameters, and lens distortion coefficients from a set of stereocamera checkerboard images. 

This project was completed as a course assignment for the School of Electrical and Computer Sciences at IIT Bhubaneswar.

## Features
* **Dynamic Grid Auto-Detection:** Automatically scans and tests multiple candidate grid sizes (e.g., 6x5, 11x8) using various image processing techniques (histogram equalization, multi-scale resizing) to maximize successful detections across imperfect datasets.
* **Sub-Pixel Corner Refinement:** Utilizes `cv2.cornerSubPix` to refine detected corners to fractional pixel accuracy, drastically lowering reprojection error.
* **Comprehensive Metrics:** Calculates and outputs both the overall Root Mean Square (RMS) error and the average per-image Mean Reprojection Error.
* **Auto-Undistortion:** Automatically generates and saves an undistorted sample image based on the calculated camera matrix.


## 🛠️ Prerequisites

Ensure you have **Python 3.x** installed along with the following standard computer vision libraries:

```bash
pip install opencv-python numpy matplotlib
```

---

## 🚀 How to Execute the Code

You can run this code either:

* **Locally on your machine**
* **In a cloud notebook environment** (Kaggle or Google Colab)

---

## Option A: Running Locally (Terminal / Command Prompt)

1. **Extract the submission ZIP file** to a local directory.

2. **Open the script** in any editor or IDE:

   ```
   full_camera_calibration_auto_detect.py
   ```

3. **Locate the `USER CONFIGURATION` section** at the very top of the script.

4. **Update the image path** to point to the sample images folder:

```python
image_path_glob = './data/leftcamera/*.png'
```

5. **Run the script from the terminal:**

```bash
python full_camera_calibration_auto_detect.py
```

---

## Option B: Running in Kaggle / Google Colab

1. Upload the script:

```
full_camera_calibration_auto_detect.py
```

2. Upload the **sample images folder** to the working directory or dataset input folder.

3. Update the image path variable. Example for **Kaggle**:

```python
image_path_glob = '/kaggle/input/your-dataset-name/data/imgs/leftcamera/*.png'
```

4. **Run the notebook cell.**

Matplotlib will automatically display the **corner detection visualizations inline**.


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

