# IT254-Security-Project
IT254 Raspberry Pi5 AI hardware pipeline

# AI-Hardware Pipelines: Camera & Pan Tracking Project

Individual project for **AI-Hardware Pipelines** (`10/12/2026` demo series), covering USB webcam capture, object/person detection, and horizontal pan tracking with a servo bracket.

## Hardware, Environment & Models
- **Device & Login (Pi 5):** Raspberry Pi 5 (`it254security`), working directory `pi5_vision_project` with virtual environment `venv` (`source venv/bin/activate`).
- **Camera & Hardware:** USB webcam (`cv2.VideoCapture` / `camera_sources.py`), horizontal pan servo bracket concept, and serial interface (`115200` baud) sending `<T:err_x,kp,deadzone,max_step>`, `<J:d_pan>`, and `<HOME>`.
- **Models & References:**
  - Hugging Face model: `facebook/detr-resnet-50` (referenced in `test_vision.py` and the threaded Pi 5 tracker)
  - Hugging Face spaces noted: `nvidia/LocateAnything`, `ustc-community/d-fine-object-detection`
  - VLM note: `LFM2.5-VL-3B` bounding box discussion
  - Updated `11/17` script: `yolov8n.onnx` (`320x320` input) with `onnxruntime` and `PyQt6`

## Repository Contents
- Project code (`test_vision.py`, threaded Pi 5 tracking script, and the `11/17` `PyQt6` + `yolov8n.onnx` pan tracker script; kept as-is without modifying the code)
- Data / model references (`facebook/detr-resnet-50`, `yolov8n.onnx`, and any test captures/data used)
- `README.md` (project overview, setup steps, demo verification notes, and bottlenecks/tips)
- `media/` (photos and/or video showing the working pipeline and hardware setup)

## Setup & Running
1. Connect to Wi-Fi and open a terminal on the Pi 5 (or your run environment).
2. Navigate to the project folder and activate the virtual environment:
   ```bash
   cd pi5_vision_project
   source venv/bin/activate

## Raspberry Pi5 config Issues
- **Camera Jitter:** The camera feed was a little jittery during testing/tracking, which affected how smooth the tracking behavior felt.
- **Imports & Package Installation:** We had to repeatedly install/download the required Python import packages to get the scripts running smoothly in the environment.
- **Single-Target Selection (Closest Person):** Instead of tracking multiple people at once, we updated the logic so the camera tracks only the closest person to the camera.
