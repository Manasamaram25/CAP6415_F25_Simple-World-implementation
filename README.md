# Simple World Implementation

## Abstract
This project implements a basic vision system for the Blocks World scene. The main goal is to process input images of colored blocks, detect edges, and lay the foundation for 3D scene reconstruction—all using classical computer vision algorithms.

## Framework
- Language: Python  
- Libraries: OpenCV, NumPy, Matplotlib

## Code
- All code for preprocessing and edge detection is contained in the repository.
- Input images are analyzed step by step from grayscale conversion to edge detection.

## Attribution
- Based on techniques in “Foundations of Computer Vision” by Torralba, Isola, Freeman.
- Uses OpenCV (https://opencv.org/) and NumPy (https://numpy.org/) for processing.

## How to Run
1. Clone the repository.
2. Place your input images in the data folder.
3. Run the Python scripts in the code folder.
4. Results are saved to the results folder.



## Results
The results folder contains processed images for each pipeline step, useful for analysis and reporting.



# #Simple World Implementationn

## Overview

This project implements a basic vision pipeline to preprocess and analyze images from a simple World. It performs grayscale conversion, blurring, edge detection, and line classification for multiple images. All steps are automated and results for each image are saved and visualized.


## Folder Structure

```
#Simple World-vision/
│
├── code/
│   └── #Simple World Implementationn.py
├── data/
│   └── (place all input images here)
├── results/
│   └── (outputs for each processed image)
├── requirements.txt
└── README.md
```



## Dependencies

- Python 3.10 or compatible
- numpy==1.24.4
- matplotlib==3.7.1
- opencv-python==4.12.0

Install dependencies using pip:

```
pip install -r requirements.txt
```

Or, recommended with conda:

```
conda create -n visionenv python=3.10
conda activate visionenv
conda install numpy=1.24 matplotlib opencv
```



## How to Run

1. Place your images in the `data/` folder and update the `image_filenames` list in `#Simple_World_Implementationn.py` with the correct file paths.
2. Run the script:
   ```
   python code/#Simple_World_Implementationn.py
   ```
   Or, open it in Jupyter Lab to step through and see the outputs interactively.

3. Generated results will be saved in the `results/` folder.  
   - Each output (`original`, `gray`, `blurred`, `edges`, `lines`) is named for its corresponding input image.


## Example Outputs

Example: For an image named `image3.gif`, results will appear as:
- `results/image3_original.png`
- `results/image3_gray.png`
- `results/image3_blurred.png`
- `results/image3_edges.png`
- `results/image3_lines.png`


## Features

- Batch processing of any number of images.
- Well-visualized results after each processing step.
- Clear code documentation and separation of files.


## Project Structure Commentary

- `code/#Simple_World_Implementationn.py`: main script with all processing steps, fully commented.
- `data/`: user-provided block world images.
- `results/`: automatically generated, organized outputs for documentation and review.


## Troubleshooting

- If your environment gives numpy errors, create a fresh conda environment as shown above.
- Be sure file paths match your operating system (Windows uses `\\`, Linux/Mac uses `/`).

