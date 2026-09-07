# Detecting-Skin-Trematodes

Skin_Trematodes_Detection.ipynb has a browser interface for video tracking, movement metrics, and configureable wavy behavior analysis. Run the included notebook in Google Colab to launch the dashboard.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://github.com/MehekBajaj/Detecting-Skin-Trematodes/blob/main/Skin_Trematodes_Detection.ipynb)

# Features
- Select a video clip, processing resolution, and track filters.
- Follow processing progress and stage updates.
- Compare source and annotated video views.
- Preview movement metrics and download the complete tracking CSV.
- Explore behavior timelines, trajectories, and frame snapshots.
- Adjust nine behavior parameters and restore defaults.
- Rerun behavior analysis with existing data.

# Instruction
1. Click Open in Colab above.
2. Select Runtime -> Change runtime type and choose a GPU runtime (A100).
3. Run all code cells from top to bottom. Initial setup installs dependencies.
4. Open the Gradio link printed by the final cell and enter the displayed username and password.
5. Upload a video, choose the clip range and filters, then select Analyze movement.
6. Open Behavior analysis, adjust parameters if needed, and select Analyze behavior.

Keep the final cell running while using the dashboard. The Gradio Link is temporary. Github hosts the notebook; the application runs during the session.

# Behavior parameters
Wavy labels are determined from recent signed-curvature direction changes. Speed and Acceleration measurements do not determine the labels.
RED = wavy
Gray = non-wavy

## Default behavior parameters
| Parameter | Default | What it controls
|---|---:|
| Clustering distance | 70 px | 
| Maximum frame gap | 3 frames |
| Minimum segment length | 15 frames |
| Smoothing window | 9 frames |
| Curvature threshold | 0.004 |
| Minimum step | 3 px/frame |
| History window | 30 frames |
| Minimum direction flips | 2 |
| Minimum object length | 10 judged frames |
