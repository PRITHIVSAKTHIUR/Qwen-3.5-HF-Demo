# **[Qwen-3.5-HF-Demo](https://huggingface.co/spaces/prithivMLmods/Qwen-3.5-HF-Demo)**

This demo application provides an interactive Gradio-based interface for exploring the multimodal capabilities of the Qwen/Qwen3.5-2B model from Hugging Face. Built with a focus on accessibility and real-time interaction, it enables users to perform a variety of vision-language tasks on images and videos, including free-form querying, caption generation, 2D point localization, object detection, video question answering, and temporal point tracking. The interface leverages advanced features such as token-by-token streaming for responsive outputs, customizable sampling rates for video processing, and visual annotations using the Supervision library to overlay bounding boxes, masks, and keypoints directly on media. Designed for developers, researchers, and enthusiasts in computer vision and natural language processing, the app runs efficiently on GPU-accelerated environments via Hugging Face Spaces, with fallback support for CPU execution. It incorporates a custom Steel Blue theme for an intuitive user experience, complete with dynamic graph panels for monitoring sampling metrics and progress indicators for long-running inferences. By integrating tools like OpenCV for frame extraction and PIL for image manipulation, the demo showcases practical applications of Qwen 3.5 in real-world scenarios, such as analyzing environmental scenes, tracking objects in dynamic footage, or generating descriptive summaries, all while maintaining a lightweight footprint suitable for local deployment or cloud hosting.

> [!IMPORTANT]
Demo: https://huggingface.co/spaces/prithivMLmods/Qwen-3.5-HF-Demo

---

<img width="1918" height="2359" alt="Screenshot 2026-03-07 at 09-03-44 Qwen 3 5 HF Demo - a Hugging Face Space by prithivMLmods" src="https://github.com/user-attachments/assets/29e0b7ec-15be-496f-ba79-0a275014ca3d" />
<img width="1918" height="1830" alt="Screenshot 2026-03-07 at 09-02-01 Qwen 3 5 HF Demo - a Hugging Face Space by prithivMLmods" src="https://github.com/user-attachments/assets/46812fb9-e3d4-4ef5-88a2-fcab87dddc8e" />

---

## Features

- **Image Understanding Tab**: Upload images to query content, generate captions of varying lengths, localize specific points (e.g., object features), or detect bounding boxes for specified targets. Outputs include annotated images with keypoints or masks and JSON-formatted results.
- **Video QA Tab**: Process short videos (up to 7 seconds recommended) with natural language questions, sampling key frames for contextual reasoning. Supports direct video input via Qwen VL utils or manual frame extraction as a fallback.
- **Video Detection Tab**: Detect objects across sampled video frames at configurable FPS rates (0.1–48.0) and frame caps (1–120), producing an annotated output video with overlaid bounding boxes and a gallery of key-frame results, plus detailed JSON summaries.
- **Video Point Tracking Tab**: Track 2D points (e.g., specific landmarks) over time in videos, rendering red tracking dots on the full video and key frames, with per-frame timestamps and point data exported as JSON.
- **Real-Time Streaming**: All text generations stream tokens live, providing immediate feedback during inference.
- **Custom UI Elements**: Includes interactive sliders for sampling control, metric visualization panels estimating frame counts for different video durations, and responsive CSS styling with dark mode support.
- **Error Handling and Progress Tracking**: Built-in validation for inputs, progress bars for batch processing, and GPU memory management for stable performance.

## Installation

To run this demo locally, follow these steps:

1. **Clone the Repository**:
   ```
   git clone https://github.com/PRITHIVSAKTHIUR/Qwen-3.5-HF-Demo.git
   cd Qwen-3.5-HF-Demo
   ```

2. **Set Up Environment**:
   - Ensure Python 3.10+ is installed.
   - Create a virtual environment (recommended):
     ```
     python -m venv venv
     source venv/bin/activate  # On Windows: venv\Scripts\activate
     ```

3. **Install Dependencies**:
   - First, upgrade pip (from pre-requirements.txt):
     ```
     pip install --upgrade pip>=23.0.0
     ```
   - Then install all requirements (from requirements.txt):
     ```
     pip install -r requirements.txt
     ```
   Note: Some dependencies (e.g., accelerate, peft) are installed via Git URLs for the latest versions. If you encounter issues with `qwen-vl-utils`, ensure it is installed for optimal video processing; otherwise, the app falls back to manual frame extraction.

4. **Optional: GPU Setup**:
   - For CUDA acceleration, install PyTorch with CUDA support if not already included via the requirements:
     ```
     pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
     ```
   The app auto-detects CUDA availability and uses bfloat16 precision where supported.

## Usage

1. **Launch the App**:
   ```
   python app.py
   ```
   This starts the Gradio server, typically accessible at `http://127.0.0.1:7860`. For sharing, use `demo.launch(share=True)` (requires Gradio account).

2. **Navigate Tabs**:
   - **Image Understanding**: Select a category (Query, Caption, Point, Detect), upload an image, provide a prompt, and click "Process Image". View streamed text and annotated visuals.
   - **Video QA**: Upload a video, enter a question, and click "Analyze Video" for a streamed summary.
   - **Video Detection/Point Tracking**: Upload a video, specify the target, adjust sampling sliders (updates metrics in real-time), and click the process button. Outputs include annotated videos, galleries, and JSON exports.

3. **Examples**:
   - The interface includes example buttons for quick testing with sample media (ensure `examples/` folder is populated).
   - For videos, keep durations under 7 seconds to avoid frame cap issues; adjust sliders for longer clips.

4. **Customization**:
   - Modify `MODEL_NAME` in `app.py` to switch models (e.g., larger Qwen variants).
   - Edit CSS in the `css` variable for theming tweaks.
   - For production, deploy on Hugging Face Spaces by uploading the repo.

## Limitations

- Video processing is optimized for short clips (max ~7s at 1 FPS sampling) due to frame limits and inference time.
- Detection accuracy depends on prompt clarity and model capabilities; results are normalized to [0,1] coordinates.
- Requires significant VRAM (4GB+ recommended) for smooth GPU operation; CPU fallback is slower.
- No real-time video input; all processing is offline.

## License

This project is licensed under the Apache License, Version 2.0. See the [LICENSE](LICENSE) file for details.

## Repository

- GitHub: [https://github.com/PRITHIVSAKTHIUR/Qwen-3.5-HF-Demo.git](https://github.com/PRITHIVSAKTHIUR/Qwen-3.5-HF-Demo.git)
- Contributions welcome via pull requests. For issues, open a ticket on GitHub.
