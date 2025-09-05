# Helmet and Number Plate Detection using YOLOv12

[![Project Demo](https://img.youtube.com/vi/Y-1EDpcoLG4/0.jpg)](https://youtu.be/Y-1EDpcoLG4)

## Overview
This project demonstrates real-time detection of helmets, no-helmet cases, and number plates in video streams using a custom-trained YOLOv12 model. It also integrates Google Gemini (via LangChain) for automatic number plate text extraction, providing a complete pipeline for safety compliance and automated monitoring.  

The system is designed for research, deployment, and real-world applications such as traffic safety enforcement and workplace compliance monitoring.  

## Features
- Real-time detection of helmets, no-helmet cases, and number plates  
- YOLOv12 custom-trained model for high accuracy  
- Automated number plate recognition using Google Gemini  
- Threaded analysis for efficient multi-frame processing  
- Logging system for number plates with timestamps and track IDs  
- Easily adaptable codebase for research or production deployment  

## Requirements
- Python 3.10 or higher  
- NVIDIA GPU with CUDA support (recommended for real-time inference)  
- Roboflow account (for dataset management and retraining)  
- Google API Key (for Gemini integration, stored in `.env`)  

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ThiruvarankanM/AI-Based-Helmet-Plate-Recognition.git
   cd Helmet_Plate_Detection
   ````

2. Create and activate a virtual environment (recommended):

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate   # Linux/Mac
   .venv\Scripts\activate      # Windows
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Configure environment variables:

   * Create a `.env` file in the project root with the following content:

     ```
     GOOGLE_API_KEY=your_api_key_here
     ```

5. Place resources:

   * YOLOv12 model weights: `best.pt` (project root)
   * Input video: `Helmet_NumberPlate.mp4` (project root)

## Dataset and Training

* Dataset is managed through Roboflow.
* Use the provided Jupyter notebook (`Helmet_Plate_Detection.ipynb`) to download the dataset.
* Train with Ultralytics YOLOv12:

  ```bash
  yolo task=detect mode=train model=yolov12s.pt data=path/to/data.yaml epochs=100 imgsz=640 plots=True
  ```
* After training, place the best model weights (`best.pt`) in the project root for inference.

## Usage

Run the application:

```bash
python app.py
```

The script will process the video, detect helmets and number plates, crop number plate regions, send them to Gemini for recognition, and log the results to `numberplate_log.txt`.

Press `ESC` to exit the application.

## File Structure

```
Helmet_Plate_Detection/
│── app.py                       # Main application script
│── best.pt                      # YOLOv12 model weights
│── Helmet_NumberPlate.mp4       # Input video
│── requirements.txt             # Python dependencies
│── numberplate_log.txt          # Output log file
│── Helmet_Plate_Detection.ipynb # Dataset download and training notebook
│── .env                         # Google API key (excluded from Git)
```

## Customization

* To use a different video, update the filename in `app.py` or replace `Helmet_NumberPlate.mp4`.
* Detection intervals and crop sizes can be adjusted in `app.py`.
* For retraining, update the Roboflow project/version in the notebook and follow the training steps.

## Notes

* The YOLOv12 model is trained for three classes: `helmet`, `no-helmet`, and `numberplate`.
* High-quality input video and well-annotated datasets improve results.
* Google Gemini is used for accurate number plate text extraction.

## License

This project is provided for educational and research purposes. Please review the repository for detailed license terms.
