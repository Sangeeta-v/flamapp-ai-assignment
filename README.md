# Flamapp.AI Assignment — <Sangeeta>

**Repository:** https://github.com/<Sangeeta>/flamapp-ai-assignment  
**Assignment:** Flamapp.AI — First round interview submission  
**Last updated:** 2025-11-14

---

## 1. Overview
A minimal proof-of-concept demonstrating an Android app + Web UI where camera frames are processed using native C++ (NDK) with OpenCV via JNI. The app shows a real-time processing pipeline (Camera → JNI → OpenCV → Display). The web app demonstrates the same algorithm via image upload (OpenCV.js) or shows recorded output.

---

## 2. Features implemented
- **Android**
  - Camera capture (CameraX) → send frames to native code via JNI.
  - Native C++ (NDK) uses OpenCV for simple real-time processing (example: Canny edge detection / contour overlay).
  - Processed frames rendered back to UI.
- **Web**
  - React + TypeScript small app with image upload and client-side processing (OpenCV.js) **OR** static demo pages showing Android results.
- **Documentation**
  - Setup steps for NDK and OpenCV.
  - Architecture explanation and frame flow.
  - Screenshots and GIF of the working app.

---

## 3. Repo structure
/ (root)
├─ android-app/ # Android Studio project (Kotlin)
│ ├─ app/src/main/java/...
│ ├─ app/src/main/cpp/... # native C++ files (JNI)
│ ├─ app/src/main/jniLibs/ # prebuilt .so (optional)
│ └─ CMakeLists.txt
├─ web-app/ # React + TypeScript demo
├─ docs/
│ ├─ screenshot-1.png
│ └─ demo.gif
├─ README.md
└─ link.txt # (optional) contains this repo URL for form upload


---

## 4. Architecture & frame flow
**High level**
- **Android UI (Kotlin)** → **CameraX** captures frames → **JNI** bridge (`processFrame(byte[] data, int w, int h)`) → **Native C++ (NDK)** uses OpenCV (`cv::Mat`) to process → processed bytes/bitmap returned → UI displays processed image.

**Frame flow**
1. CameraX → `ImageProxy` → convert to NV21/RGBA bytes  
2. Kotlin calls `native processFrame(...)`  
3. C++: `jbyteArray` → `cv::Mat` → process → encode to RGBA bytes → return `jbyteArray`  
4. Kotlin: bytes → Bitmap → ImageView

---

## 5. Android setup (build & run)
**Prerequisites**
- Android Studio (Arctic Fox or later)
- JDK (bundled with Android Studio)
- NDK (install via SDK Manager) — recommended NDK r25+
- CMake (install via SDK Manager)
- OpenCV Android SDK

**Steps**
1. Clone:
   ```bash
   git clone https://github.com/<Sangeeta>/flamapp-ai-assignment.git
   cd flamapp-ai-assignment/android-app
