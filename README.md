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
| Parameter | Default | What it means |
|---|---:|---|
| Clustering distance | 70 px | Distance used to connect neighboring tracking points into object clusters. 
Larger values can merge nearby groups; smaller values can separate them. |
| Maximum frame gap | 3 frames | Largest allowed difference between successive observed frame numbers within one segment. A value of 3 allows up to two missing frames to be interpolated. Larger gaps split the trajectory. |
| Minimum segment length | 15 frames | Minimum trajectory length needed for behavior analysis, including interpolated frames. Increasing this excludes shorter segments. |
| Smoothing window | 9 frames | Number of frames used to estimate curvature with smoothing. Larger windows can reduce jitter but smooth away brief bends. Must be odd, at least 5, and no larger than the minimum segment length. |
| Curvature threshold | 0.004 | Curvature magnitude a bend must exceed to count as a left or right bend. Lower values include gentler bends; higher values ignore them. |
| Minimum step | 3 px/frame | Minimum smoothed movement per frame needed to retain curvature. Below this value, curvature is set to zero. Increasing it suppresses more slow or nearly stationary movement. |
| History window | 30 frames | Number of recent frames used to count bending-direction changes, including the current frame. Larger windows retain earlier changes for longer. |
| Minimum direction flips | 2 | Minimum median flip count across an object's assessed tracking points required to label that object-frame wavy. Higher values require more repeated changes in bending direction. |
| Minimum object length | 10 judged frames | Minimum number of assessed frames required for an object to appear in the summary and timeline. These frames do not need to be consecutive or wavy. |
