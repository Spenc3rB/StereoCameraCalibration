# Camera Calibration and Stereo Calibration README

This repository contains Python scripts for calibrating individual cameras and performing stereo calibration using OpenCV. The calibration process involves obtaining intrinsic parameters for each camera and determining the transformation between the two cameras in a stereo setup. The parameters are saved as a file `stereoMap.xml` and in the camera_parameters directory. 

## Prerequisites

- Python 3.x
- OpenCV (cv2)
- NumPy
- SciPy
- PyYAML

## Usage

1. Install the required dependencies:

```bash
pip install opencv-python numpy scipy
```

2. Run the script with the calibration settings file:

```bash
python calibrate.py calibration_settings.yaml
```

Make sure to replace `calibration_settings.yaml` with the actual path to your calibration settings file.

## Calibration Steps

### Step 1: Save Calibration Frames for Single Cameras

- Save frames for each camera separately using the `save_frames_single_camera` function.

### Step 2: Obtain Camera Intrinsic Matrices

- Calibrate each camera individually to obtain intrinsic matrices using the `calibrate_camera_for_intrinsic_parameters` function.

### Step 3: Save Calibration Frames for Both Cameras Simultaneously

- Save frames for both cameras simultaneously using the `save_frames_two_cams` function.

### Step 4: Stereo Calibration

- Use paired calibration pattern frames to obtain the rotation and translation between camera0 and camera1 with the `stereo_calibrate` function.

### Step 5: Save Calibration Data

- Save the calibration data, where camera0 defines the world space origin, using the `save_extrinsic_calibration_parameters` function.

### Optional: Define a Different Origin Point

- Optionally, you can define a different origin point and save the calibration data using the `get_world_space_origin` and `get_cam1_to_world_transforms` functions.

## File Descriptions

- `calibrate.py`: Main script for camera calibration and stereo calibration.
- `calibration_settings.yaml`: YAML file containing calibration settings such as camera parameters, frame dimensions, checkerboard size, etc.
- `camera_parameters/`: Directory to store the camera intrinsic and extrinsic calibration parameters.

## Output

- The script will generate various output files, including camera intrinsic parameters, stereo calibration parameters, and extrinsic parameters defining the transformation between cameras.

## Notes

- Make sure to adjust the `calibration_settings.yaml` file to match your specific setup.

## Acknowledgements

- A lot of this code is derived and redeveloped from [TemugeB's repository on github](https://github.com/TemugeB/python_stereo_camera_calibrate)

## License

This project is licensed under the [Apache 2.0 license](LICENSE).
