# Character Builder

A single-file, in-browser editor for tweaking an illustrated character. Upload a PNG (or drop one on the stage), then reshape and restyle it with live sliders and export a 4:5 PNG. It runs entirely in your browser: nothing is uploaded anywhere.

Open `index.html` in a modern browser. No build step, no dependencies to install.

## Demo

See Character Builder in action:

https://github.com/user-attachments/assets/4f3a8a1a-7d35-4bda-bf33-52a4ee14d739

[Download the MP4](assets/character-builder-demo.mp4)
## Features

- **Characters rail:** keep several characters, each with its own settings. **Save** snapshots the current look as a new tile.
- **Head size:** drag the dashed **Head** circle over the face to place it, resize it with the handle, then use the slider.
- **Body shape** (lean to sturdy) and **Height** (legs), applied with a smooth three-band warp (head, torso, legs).
- **Colour lighting:** tint the whole character while keeping its shading, with a strength slider.
- **Background:** transparent, solid or gradient, with custom top and bottom colours.
- **Hold to see original**, **Undo** (Ctrl+Z), **Back to original**, zoom, drag to pan.
- **Download PNG:** 1080 x 1350 (4:5), transparent where the background is.
- **Background removal:**
  - *AI cutout* (best for photo-like images) runs in the browser using [`@imgly/background-removal`](https://github.com/imgly/background-removal-js). The first run downloads a model; the image never leaves your device.
  - *Colour cutout* handles flat-colour backgrounds, with a tolerance slider.
  - Images that already have a transparent background are used as-is.
- **3D mode (optional):** attach a `.glb` model to a character and switch to **3D**. The same head, body and height sliders reshape the mesh, colour lighting becomes real coloured lights, and you can drag to rotate. A free way to make a `.glb` from your PNG is [TRELLIS on Hugging Face](https://huggingface.co/spaces/microsoft/TRELLIS).

## Tips for best results

- Use a full-body, front-facing character in a neutral standing pose. Stylised characters (3D toy, anime, clay) work best.
- Prompt your image generator for a transparent or plain flat background.
- If the head slider drags the shoulders along, move the Head circle so its bottom edge sits just under the chin.

## Notes and limitations

- It's a 2D warp, not a rig: strong settings can distort complex poses.
- The page loads Inter from Google Fonts, and three.js and the background-removal library from jsDelivr, only when needed. Fonts fall back to system fonts when offline, and 2D editing with an already transparent PNG works offline.
- Exports are generated in the browser; if a download is blocked (for example inside a sandboxed frame), the export dialog also shows the image so you can save it manually.
- The built-in sample character is drawn in code, so the repo contains no third-party artwork.

## Run locally

```bash
# any static server works, or just double-click index.html
npx serve .
```
