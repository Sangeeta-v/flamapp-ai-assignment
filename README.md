# flamapp-ai-assignment
Assignment for Flamapp.AI first round interview
# Flamapp.AI Assignment — <Your Name>

**Repository:** https://github.com/<your-username>/flamapp-ai-assignment  
**Assignment:** Flamapp.AI — First round interview submission  
**Last updated:** YYYY-MM-DD

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
