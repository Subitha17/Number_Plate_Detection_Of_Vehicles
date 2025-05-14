                                                            Number_Plate_Detection_Of_Vehicl
Here’s a well-structured `README.md` for your **License Plate Detection and Recognition** project in Google Colab:

---

# 🚘 Real-Time License Plate Detection & Recognition (Google Colab)

This project performs automatic **license plate detection and recognition** on uploaded images and videos. It uses **OpenCV** for image processing and **EasyOCR** for Optical Character Recognition (OCR). It’s optimized to run in **Google Colab** and includes support for both **images and video files**.

---

## 🧰 Features

* 📷 Detects license plates in uploaded images and videos.
* 🧠 Recognizes text from license plates using EasyOCR.
* 💾 Saves and allows downloading of processed output (images/videos).
* 🎞️ Video support with frame-by-frame processing and performance logging.
* ✅ Google Colab compatible, including automatic file uploads and downloads.

---

## 📦 Requirements

Install all necessary dependencies in Colab:

```python
!pip install opencv-python-headless easyocr imutils numpy matplotlib
!apt-get update && apt-get install -y libgl1-mesa-glx
```

If using video processing and conversion:

```python
!pip install ffmpeg-python
```

---

## 📂 File Structure

```
license_plate_recognition/
│
├── main.py           # Main script (provided above)
├── README.md         # This file
```

---

## 🧪 How It Works

### 🔍 1. Detect Plate

Uses **OpenCV** techniques:

* Grayscale conversion
* Bilateral filtering (denoising)
* Canny edge detection
* Contour detection and approximation (for 4-sided plates)

```python
location = detect_plate(image)
```

---

### 🔠 2. Recognize Text

Uses **EasyOCR** to extract text from the detected plate region.

```python
result = reader.readtext(plate_region)
```

Text is cleaned using regex to remove non-alphanumeric characters.

---

3. Process Images
Detects license plates from uploaded image files (`.jpg`, `.png`, etc.), overlays bounding boxes and recognized text, and allows download.

4. Process Video
Processes uploaded video files (`.mp4`, `.avi`, `.mov`) frame by frame:

* Processes every 5th frame for efficiency.
* Overlays plate bounding boxes and recognized text.
* Outputs annotated video for download.

Also provides:
* FPS monitoring
* Codec fallback handling
* File size validation

Google Colab Integration
* Uses `google.colab.files.upload()` for uploading files.
* Uses `cv2_imshow()` to display frames.
* Uses `files.download()` to allow downloading processed results.

Example Workflow
In **Colab**, run the full notebook or execute:
                      main()

Then upload either:
* 📷 Image (`.jpg`, `.png`)
* 🎥 Video (`.mp4`, `.avi`, `.mov`)

Sample Output:
Detected license plate: MH12AB1234
Video properties: 1280x720 at 30.0 FPS
Processed 150 frames. FPS: 22.31. Last plate: MH12AB1234
Output saved as output_video.mp4

Notes
* **GPU acceleration** is enabled for OCR (`gpu=True`).
* Real-time webcam access is not available in Google Colab — use uploaded files.
* This code uses synthetic frame skipping for performance (every 5th frame).
* OCR may produce inaccurate results under poor lighting or motion blur.
* Use higher quality videos/images for better accuracy.

Future Improvements
* Fine-tune plate detection using deep learning (YOLO or SSD).
* Integrate real-time webcam capture (for local environments).
* Expand OCR support for multilingual plates.
* Use tracking algorithms to persist recognition across frames.

License
     This project is for educational purposes. Dependencies like OpenCV, EasyOCR, and FFmpeg are governed by their respective open-source licenses.
