# **Qwen-3.5-HF-Demo**

Qwen-3.5-HF-Demo is an experimental, advanced multimodal intelligence interface built on top of Alibaba Cloud's state-of-the-art `Qwen/Qwen3.5-2B` foundation model. Designed as a flexible multi-modal sandbox, this application unifies four complex spatial and temporal reasoning workflows: **Image Understanding**, **Video Question Answering**, **Video Object Detection**, and **Video Point Tracking**.

The platform features cross-library acceleration by coupling Hugging Face transformers with the `supervision` computer vision suite to draw clean object masks, bounding boxes, and point trajectories directly onto temporal frame buffers. Operating inside a custom, fully responsive Steel Blue workspace layout, it serves as a lightweight developer sandbox for mapping the boundaries of next-generation vision-language models.

<img width="1616" height="1768" alt="screencapture-huggingface-co-spaces-prithivMLmods-Qwen-3-5-HF-Demo-2026-07-02-21_47_47" src="https://github.com/user-attachments/assets/b9226142-bfc6-4d3d-9226-a6f744112784" />

### **Key Features**

* **Comprehensive Image QA & Grounding:** Instantly process image uploads for descriptive captioning, open-ended visual queries, exact object bounding boxes (`Detect`), or keypoint coordinate tracking (`Point`).
* **Denoised Token Streaming:** Integrates a background thread worker and a `TextIteratorStreamer` loop to output textual reasoning tokens continuously to the UI frontend.
* **Temporal Video Mask Propagation:** Samples keyframes sequentially at customizable frame rates, executes targeted detection or tracking prompts across the frame array, and utilizes OpenCV writers to rebuild an annotated video overlay file.
* **Visual Metric Graph Panel:** Houses an inline dashboard component that automatically calculates metrics like video duration, sampled frames, resolution boundaries, and down-stream loop capacities.
* **Steel Blue Aesthetic Layer:** Crafted using custom web fonts (`Outfit` & `IBM Plex Mono`), tailored card boundaries, and self-pulsing real-time execution status indicators.

### **Repository Structure**

```text
├── examples/
│   ├── 1.jpg
│   ├── 1.mp4
│   ├── 2.JPG
│   └── 2.mp4
├── app.py
├── LICENSE.txt
├── pre-requirements.txt
├── pyproject.toml
├── README.md
└── requirements.txt

```

### **Installation and Requirements**

To initialize the Qwen-3.5-HF-Demo framework locally, configure a **Python 3.10 or higher** environment with the exact deep learning wheels listed below. A system containing a modern, dedicated CUDA-capable GPU is highly recommended for smooth transformer matrix operations.

This repository runs with **PyTorch 2.8.0 or above** for better compatibility.

#### **Running with `uv` (Recommended)**

`uv` is an ultra-fast Python package and project manager written in Rust, which guarantees immediate virtual environment synchronization and reproducible execution loops.

**Step 1 — Install `uv`**

* **macOS / Linux:** `curl -LsSf [https://astral.sh/uv/install.sh](https://astral.sh/uv/install.sh) | sh`
* **Windows:** `powershell -c "irm [https://astral.sh/uv/install.ps1](https://astral.sh/uv/install.ps1) | iex"`

**Step 2 — Clone the repository**

```bash
git clone https://github.com/PRITHIVSAKTHIUR/Qwen-3.5-HF-Demo.git
cd Qwen-3.5-HF-Demo

```

**Step 3 — Initialize the project and install dependencies**

```bash
uv sync

```

**Step 4 — Run the script**

```bash
uv run app.py

```

---

#### **Standard PIP Installation**

**1. Upgrade Package Manager**
Ensure your local system installer is completely up-to-date:

```bash
pip install pip>=26.1.2

```

**2. Core Dependency Pull**
Install the primary deep learning stack, vision utilities, and video processing configurations from your local `requirements.txt` file:

```bash
pip install -r requirements.txt

```

#### **Core Requirements List (`requirements.txt`)**

```text
git+https://github.com/huggingface/accelerate.git
git+https://github.com/huggingface/peft.git
transformers-stream-generator
transformers==5.9.0
huggingface_hub
qwen-vl-utils
sentencepiece
opencv-python
torchvision
supervision
molmo_utils
matplotlib
requests
hf_xet
einops
spaces
pillow
gradio==6.19.0
torch
timm
av

```

### **Usage**

Once the web deployment initializes, open your browser to the local address provided in your terminal output (typically `[http://127.0.0.1:7860/](http://127.0.0.1:7860/)`).

1. **Image Understanding Tab:** Drag and drop an image asset into the canvas, select a task category (e.g., `Detect`), write a custom target query (e.g., *"the headlights"*), and click **Process Image** to stream text answers and view bounding box layers.
2. **Video QA Tab:** Drop a short video clip, write an evaluation prompt (e.g., *"What is happening in this video?"*), and click **Analyze Video** to extract multi-frame textual summaries.
3. **Video Detection & Tracking Tabs:** Upload video clips (recommended duration $\le 7$ seconds), specify target parameters, adjust the **Sample FPS** slider and **Max Frames** slider, and execute. The metrics module will immediately map your sampling configuration onto a live chart.

### **Links and Source**

* **License:** [Apache License 2.0](https://github.com/PRITHIVSAKTHIUR/Qwen-3.5-HF-Demo/blob/main/LICENSE.txt)
* **GitHub Repository:** [https://github.com/PRITHIVSAKTHIUR/Qwen-3.5-HF-Demo.git](https://github.com/PRITHIVSAKTHIUR/Qwen-3.5-HF-Demo.git)
* **Hugging Face Live Space:** [https://huggingface.co/spaces/prithivMLmods/Qwen-3.5-HF-Demo](https://huggingface.co/spaces/prithivMLmods/Qwen-3.5-HF-Demo)
