# MamaSight

MamaSight is a Python package for analyzing images using YOLO object detection and OCR (Optical Character Recognition). It's designed to detect UI elements and text in screenshots and provide annotated visualizations.

Originally adopted from: https://github.com/microsoft/OmniParser

## Installation

```bash
pip install mamasight
```

## Usage

```python
from mamasight import ScreenParser

# Initialize parser with custom settings
box_config = {
    'box_overlay_ratio': 3200,  # Base ratio for scaling
    'text_scale': 1.0,          # Larger text
    'text_thickness': 3,        # Thicker text
    'text_padding': 5,          # More padding around text
    'thickness': 4,             # Thicker boxes
    'annotation_style': 'simple',  # 'simple' or 'colorful'
}

# Specify a custom directory for model weights
custom_weights_path = "./model_weights"

# Initialize parser with custom weights path
parser = ScreenParser(box_config=box_config, weights_path=custom_weights_path)

# Setup - adjust device as needed ('cuda' or 'cpu'. orc_device can also be None)
parser.setup(yolo_device='gpu', ocr_device='gpu')  # Use 'cuda' if you have a GPU

# Path to test image - replace with actual path to your test image
test_image_path = "image.png"

# Analyze image with OCR
start_time = time.time()
image, detections = parser.analyze(test_image_path, use_ocr=True)
```

## Features

- Detect UI elements (icons, buttons, etc.) using YOLO
- Optional text detection with OCR
- Customizable annotation styles
- Auto GPU/CPU detection
- Returns both annotated image and structured detection data
