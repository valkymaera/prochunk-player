# Prochunk Player

**Non-linear video playback app.** (No Audio support yet)
Select frame ranges to create video "chunks", each can be duplicated, reordered,
looped, crossfaded, or time-stretched individually or in a group.

The resulting chunk timeline can be saved as a playback program or exported as recut video.

![License](https://img.shields.io/badge/license-MIT-blue)
![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![Status](https://img.shields.io/badge/status-pre--alpha-orange)

> ⚠️ **Early / pre-pilot.** This is a working prototype under active development.
> It runs from source today; a double-click desktop build is on the roadmap.
> Expect rough edges and breaking changes. Save & export features not yet implemented.

---
Prochunk has two timelines:

- The **source timeline** (TTime) - the source video's natural immutable frame sequence. You capture from this.
- The **chunk timeline** (CTime) - the arrangement of chunks captured from the source frames. This is what plays back.

You capture **chunks** from the source, arrange them on the chunk timeline, and
press play. The chunks determine the playback by referencing the source frames.
A chunk is a continguous series of frames. 

## Input Controls:
- Right-drag on the source timeline : capture a chunk from those frames.
- Left click/drag on source timeline: scrub source video time.
- Left click/drag on chunk timeline (the frame display): scrub chunk video time
- Left click a chunk to select it, Shift + Left click to multi-select neighbors
- Right click a chunk to open a context menu
- CTRL + G to group selected chunks
- CTRL + U to ungroup
- CTRL + D to duplicate a selected chunk
- CTRL + R to reverse a chunk

## Chunk Modification
- Drag the right edge to time sretch a chunk
- Drag a chunk into another to blend/crossfade

- You can specify how many times a looped chunk should loop
- You may loop the entire playback as well
  
## Purpose
This app was originally made to compare similar scenes that were scattered across a video.
Rather than manually scrub back and forth or start up a heavy after effects project, 
I wanted to just have an app where I could quickly grab frame segments and play them back
with some of them looped or stretched and some of them not. 

It has since also been useful for playback review of complex renders section by section to find errors,
as well as an alternative to side-by-side comparisons for video

## Running from source

> A packaged build isn't available yet, so for now this runs from source and
> needs Python.

Requires **Python 3.10+**.

```bash
git clone https://github.com/valkymaera/prochunk-player
cd prochunk-player

# (recommended) a virtual environment
python -m venv .venv
# Windows: .venv\Scripts\activate    |    macOS/Linux: source .venv/bin/activate

# dependencies — PyAV bundles its own ffmpeg, so nothing else to install
pip install "PySide6>=6.6" "av>=12" "numpy>=1.24"

# launch the authoring window on a clip
python examples/run_editor.py path/to/your/video.mp4
``` 

## License

[MIT](LICENSE) © Valkymaera
