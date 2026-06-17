# Face Detection Using Raspberry Pi and CircuitDigest Cloud

Face detection is a powerful technology used in security, surveillance, attendance systems, and automated target tracking. This project implements a face detection system without any complex local setup. By leveraging a Raspberry Pi, a USB camera, and the CircuitDigest Cloud Face Detection API, you can deploy a face detection application in minutes. There is no need for manual dataset collection, data labeling, or GPU-heavy local model training.

## Features
- **Real-Time Detection:** Rapidly detects faces using cloud-based AI.
- **Multiple Operating Modes:**
  - **Keyboard Mode:** Capture images manually by pressing the `SPACE` key.
  - **Auto Mode:** Automatically captures images after a fixed time interval (e.g., every 5 seconds).
  - **SSH Mode:** Runs headlessly in the terminal without opening an OpenCV window.
- **Zero Training Overhead:** Relies entirely on a pre-trained API in the CircuitDigest Cloud.
- **Multi-Face Support:** Detects and counts multiple faces within a single frame.

## Hardware Requirements
- **Raspberry Pi** (Pi 3, Pi 4, or newer, connected to external power)
- **USB Web Camera** (For capturing facial images)
- **Laptop/PC** (For initial setup and output monitoring)
- MicroSD Card (with Raspberry Pi OS installed)

## Hardware Setup
1. Place the USB Web Camera in a position with a clear view of the area being monitored.
2. Connect the USB Camera to one of the USB ports on the Raspberry Pi.
3. Ensure the Raspberry Pi is powered by a reliable external power supply.

## Software Setup
1. Setup your Raspberry Pi using the **Raspberry Pi Imager** with a standard OS installation.
2. Create an account on the [CircuitDigest Cloud](https://www.circuitdigest.cloud/).
3. Navigate to the **Face Detection** feature and copy your **API Key**.
4. Open **Thonny IDE** on your Raspberry Pi.
5. Install the necessary Python packages:
   ```bash
   pip install opencv-python requests
   ```

## Installation & Usage
1. Clone this repository or copy the Python script to your Raspberry Pi.
2. Edit the script to configure your parameters:
   ```python
   SERVER_URL = "https://www.circuitdigest.cloud/api/v1/face-detection/detect"
   API_KEY    = "YourApikey"  # <-- Paste your CircuitDigest API Key here
   MODE = "keyboard"          # <-- Set to "keyboard", "auto", or "ssh"
   AUTO_INTERVAL = 5          # <-- Interval in seconds for auto mode
   ```
3. Run the script:
   ```bash
   python face_detection.py
   ```
4. Depending on the mode selected, the system will capture images and send them to the CircuitDigest Cloud API. The total face count and confidence details will print directly to the terminal.

## Troubleshooting
- **Camera not found! Check USB camera connection:** 
  Verify the USB physical connection. If multiple camera devices are present, you may need to update the index in the script from `cv2.VideoCapture(0)` to `cv2.VideoCapture(1)`.
- **API request timeout:** 
  Check that the Raspberry Pi is connected to a stable Wi-Fi or Ethernet connection. Try increasing the timeout threshold in the code if needed.
- **Invalid API key error:** 
  Verify that your API key is copied correctly from the CircuitDigest Cloud account and paste it into the script without spaces.
- **Faces not detected properly:** 
  Ensure the camera is placed in a well-lit area and the subject is facing the camera. Blurry images or poor camera angles can affect detection.
- **Program crashes during execution:** 
  Check that the `opencv-python` and `requests` libraries are correctly installed. Restart the script or camera connection if the OpenCV frame breaks.

## Advantages & Limitations
| Advantages | Limitations |
| :--- | :--- |
| Real-time face detection using cloud-based AI | Requires a stable internet connection for processing |
| No need for model training or dataset collection | Detection accuracy depends on camera quality |
| Easy to implement using a Raspberry Pi and a USB camera | Poor lighting can reduce detection performance |
| Supports both manual (keyboard) and automatic capture modes | Cloud API usage may have daily or monthly limits |
| Useful for security, attendance, and crowd surveillance | Slight delay may occur due to network transmission |

## Link For the Full Guide

https://circuitdigest.com/microcontroller-projects/raspberry-pi-face-detection-using-circuitdigest-cloud

---

## Relevant Links
- [CircuitDigest Cloud Platform](https://www.circuitdigest.cloud/)
- [Raspberry Pi based Face Detection GitHub Repo](https://github.com/Circuit-Digest/Raspberry-Pi-based-Face-Detection)
