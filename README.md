# YOLO Real‑Time Object Detection (Webcam)

This project gives you **two ways** to run real‑time YOLO detection from your webcam:

1) **CLI (OpenCV window)** — easiest for local use  
2) **Streamlit Web App** — run in the browser with `streamlit-webrtc`


---

## 1) Quick Start (CLI)

```bash
# 1) Create and activate a virtual env (Windows PowerShell shown; use python3 on Linux/macOS)
python -m venv .venv
. .venv/Scripts/Activate.ps1   # Windows PowerShell
# source .venv/bin/activate     # Linux/macOS

# 2) Install deps
pip install --upgrade pip
pip install -r requirements.txt

# 3) Run with default COCO model (yolov8n.pt)
python app.py --source 0 --conf 0.35
```

- Press **Q** to quit.  
- Use `--source path/to/video.mp4` for a file instead of webcam.  
- Use `--weights path/to/best.pt` to use your custom model.

---

## 2) Run the Streamlit Web App

```bash
# From your virtual env
streamlit run app_streamlit.py
```
- Allow camera access in the browser.
- Use sliders to change confidence and NMS thresholds live.

---

## Training Custom Model (optional, one‑liner)

If you have annotated data in YOLO format:
```bash
yolo task=detect mode=train model=yolov8n.pt data=your_data.yaml epochs=50 imgsz=640
```
Then use the trained weights:
```bash
python app.py --weights runs/detect/train/weights/best.pt
```

---

## Files

- `app.py` — CLI real‑time detector (OpenCV window)
- `app_streamlit.py` — Streamlit real‑time detector (browser), powered by `streamlit-webrtc`
- `requirements.txt` — Dependencies
- `README.md` — This file

