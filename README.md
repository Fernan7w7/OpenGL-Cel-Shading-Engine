# Toon Shading & Outline Rendering  Engine (OpenGL)

This project implements a real-time **toon shading** and **outline rendering** pipeline in OpenGL. The goal is to recreate the stylized, flat-shaded look of hand-drawn animation using lighting quantization and silhouette extraction.
![Jet][assets/Jet_set_radio.gif]

# Features
-  Toon Shading:
   Discrete lighting levels for a cel-shaded look.

- Outline Rendering:
	- Geometry-based (backface expansion)
	- Image-space (Sobel edge detection)

- Model Support: 
  Loads OBJ models and renders them with a controllable camera.
  
- Optional Enhancements:
  Rim lighting, halftone shading, adjustable outline thickness.
  
# How It Works
## 1. Toon Shading
Lighting is computed per-fragment, then quantized into a small number of intensity bands:

`I = max(0, dot(normal, lightDir))`

Thresholds split the lighting into 2–4 flat color steps.

## 2. Outline Extraction
Two techniques are available:
- **Geometry-based:** render expanded backfaces in black
- **Image-space:** detect edges using Sobel filtering on framebuffer depth/normals
We'll test both and decide which one to use

# System Structure
- OBJ model loading
- VAO/VBO setup
- Fragment shaders for quantized lighting
- Optional post-processing pass for outlines
- Camera controls (arcball or FPS-style)

# Summary (If you are lazy)
This project builds a modular, real-time OpenGL pipeline for stylized cartoon rendering. It combines simple lighting quantization with silhouette extraction to achieve a clean, expressive NPR visual style.
