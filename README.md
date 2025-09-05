# Helmet and Number Plate Detection with Gemini AI Integration

## Overview
This project provides an end-to-end solution for detecting helmets and number plates in video streams using a YOLOv8 model, with number plate analysis powered by Google Gemini AI. The system is designed for safety compliance monitoring and automated number plate logging.

## Features
- Real-time detection of helmets, no-helmet cases, and number plates in video frames
- Automated extraction and logging of number plate information using Gemini AI
- Configurable detection intervals and video sources
- Modular and extensible Python codebase

## Requirements
- Python 3.8+
- pip (Python package manager)
- A valid Google Gemini API key

## Installation
1. **Clone the repository:**
   ```sh
   git clone <your-repo-url>
   cd Helmet_Plate_Detection
   ```
2. **Create and activate a virtual environment (recommended):**
   ```sh
   python3 -m venv .venv
   source .venv/bin/activate
   ```
3. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```
4. **Download or place your YOLOv8 model weights as `best.pt` in the project root.**
5. **Ensure your video file is named `Helmet_NumberPlate.mp4` and placed in the project root.**
6. **Set up your `.env` file:**
   - Create a file named `.env` in the project root with the following content:
     ```
     GOOGLE_API_KEY=your_actual_gemini_api_key
     ```

## Usage
Run the main application:
```sh
python app.py
```
- The script will process the video, detect helmets and number plates, and log recognized number plates to `numberplate_log.txt`.
- Press `ESC` to exit the video window at any time.

## File Structure
- `app.py` — Main application script
- `best.pt` — YOLOv8 model weights
- `Helmet_NumberPlate.mp4` — Input video file
- `.env` — Environment variables (API key)
- `requirements.txt` — Python dependencies
- `numberplate_log.txt` — Output log of detected number plates

## Customization
- To use a different video, change the filename in `app.py` or replace `Helmet_NumberPlate.mp4`.
- Adjust detection intervals and crop sizes in `app.py` as needed.

## Notes
- Ensure your Google Gemini API key is valid and has the necessary permissions.
- The YOLOv8 model should be trained to recognize the classes: helmet, no-helmet, and numberplate.
- For best results, use high-quality video input.

## License
This project is provided for educational and research purposes. Please check the repository for license details.

## Contact
For questions or contributions, please open an issue or submit a pull request on GitHub.
