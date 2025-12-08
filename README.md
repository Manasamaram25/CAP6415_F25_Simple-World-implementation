# Simple World Implementation – Computer Vision Project

## Overview

This project implements a classical computer vision pipeline for a Simple World of stacked blocks. The goal is to start from 2D images of a block‑world scene and extract useful structure: edges, lines, figure/ground separation, and a simple 3D world coordinate representation.

The pipeline uses traditional image processing techniques with OpenCV, NumPy, and Matplotlib. It is designed as a step‑by‑step implementation of concepts from introductory computer vision, without any machine learning.

## Features

- Load and preprocess multiple Simple World images.
- Convert images to grayscale and apply Gaussian blur.
- Detect edges with the Canny edge detector.
- Detect and classify straight line segments (vertical vs horizontal) using the probabilistic Hough transform.
- Perform simple figure/ground separation using thresholding and morphology.
- Construct X, Y, Z world coordinate maps over the image.
- Visualize a basic 3D surface reconstruction from these coordinates.
- Save all intermediate and final results for each image into a `results` directory.

## Project Structure

```
simple-world-implementation/
│
├── CV_Final_Project_Manasa_Maram-Final.ipynb   # Main project notebook
├── data/                                      # Input images (Simple World scenes)
│   ├── image1.png
│   ├── image2.png
│   └── ...
├── results/                                   # Auto-generated outputs (created at runtime)
│   ├── image1_gray.png
│   ├── image1_edges.png
│   ├── image1_lines.png
│   ├── image1_figure_mask.png
│   ├── image1_world_coordinates.png
│   └── ...
├── requirements.txt                           # Python dependencies
└── README.md
```

The notebook reads from `data/` and writes its outputs to `results/`.

---

## Dependencies

The project requires Python 3.10+ and the following libraries:

- `numpy`
- `opencv-python`
- `matplotlib`
- `jupyter` (for running the notebook)

Example `requirements.txt`:

```
numpy==1.24.4
opencv-python==4.10.0.84
matplotlib==3.7.1
jupyter==1.0.0
```

You may adjust versions to match your environment.

---

## Installation

1. Clone or download the repository

```
git clone https://github.com/<your-username>/simple-world-implementation.git
cd simple-world-implementation
```

2. Create and activate a virtual environment (recommended)

Using Conda:

```
conda create -n simpleworld python=3.10
conda activate simpleworld
```

Or using `venv`:

```
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows
```

3. Install dependencies

```
pip install -r requirements.txt
```

---

## Data

Place your Simple World images (PNG, JPG, GIF, etc.) into the `data/` folder, for example:

```
data/
├── simple_world_1.png
├── simple_world_2.png
└── simple_world_3.png
```

In the notebook, set the list of image filenames:

```
image_filenames = [
    "data/simple_world_1.png",
    "data/simple_world_2.png",
    "data/simple_world_3.png",
]
```

Update this list if you add or remove images.

---

## How to Run

### Option 1 – Run the notebook (recommended)

1. Start Jupyter:

```
jupyter notebook
```

2. Open `CV_Final_Project_Manasa_Maram-Final.ipynb`.

3. Run all cells from top to bottom (`Kernel → Restart & Run All`), or step through interactively.

The notebook will process each image, show intermediate figures inline, and save all outputs into the `results/` folder.

### Option 2 – Run as a Python script

If you export the main loop to a script (for example `blocks_world_processing.py`), you can run:

```
python blocks_world_processing.py
```

This will generate the same outputs in `results/` without interactive visualization.

---

## Processing Pipeline

For each image, the following steps are applied:

1. Load and preprocess
   - Read the color image from disk.
   - Convert to grayscale.
   - Apply Gaussian blur to reduce noise.

2. Edge detection
   - Run the Canny edge detector on the blurred grayscale image to obtain a binary edge map.

3. Line detection and classification
   - Use the probabilistic Hough transform to detect straight line segments.
   - Compute the orientation of each line.
   - Color vertical lines (angles near 90°) in green and horizontal lines (angles near 0° or 180°) in red.
   - Overlay these lines on the original image.

4. Figure / ground separation
   - Apply a global intensity threshold to segment figure (blocks) from background.
   - Clean the result with morphological opening and closing.
   - Use the binary mask to generate a “figure only” image containing just the blocks.

5. World coordinate maps
   - Let the image size be \(h \times w\).
   - Construct:
     - X world coordinate: values increase from left to right.
     - Y world coordinate: values increase from top to bottom.
     - Z world coordinate: set to a constant plane (flat depth) in this basic implementation.
   - Visualize X, Y, and Z as grayscale/colormapped images.

6. 3D surface reconstruction
   - Interpret X, Y, Z as a grid and plot a 3D surface.
   - With constant Z, this appears as a flat plane; in extended versions different depths can be assigned per block.

---

## Outputs

For each input image `name.ext`, typical outputs include:

- `results/name_original.png` – original color image.
- `results/name_gray.png` – grayscale image.
- `results/name_blurred.png` – blurred grayscale image.
- `results/name_edges.png` – edge map (Canny).
- `results/name_lines.png` – edge classification overlay (green vertical / red horizontal).
- `results/name_figure_mask.png` – binary figure/ground mask.
- `results/name_figure_only.png` – original image with only the figure visible.
- `results/name_world_coordinates.png` – multi-panel visualization of X, Y, Z (if saved).
- `results/name_3d_surface.png` – 3D surface reconstruction (if saved).

These outputs are intended for analysis, reports, and the final presentation video.

---

## Limitations and Future Work

- Depth model: The current Z map is flat. Future work could assign different depth values to different blocks and produce a stepped 3D reconstruction.
- **Segmentation robustness:** Figure/ground is based on a simple global threshold. Using adaptive thresholds or color clustering would improve robustness to lighting changes.
- Geometry: Only vertical and horizontal lines are distinguished. Extending the analysis to diagonal edges and junction types would provide a richer structural description.
- Camera model: The mapping from image to world coordinates assumes an orthographic model. Estimating camera parameters could enable a more realistic projection.

---

## License

This project is intended for educational use. If you publish the repository publicly, you may add a license such as the MIT License and include a `LICENSE` file.

---

## Author

Manasa Maram  
Simple World Implementation – Computer Vision Final Project
