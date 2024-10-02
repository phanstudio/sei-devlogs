---
layout: default
title: "Export your Godot to Web"
date: 2024-10-01
---

To export your Godot project as an HTML5:

### Step 1: Install Export Templates
1. **Open Godot** and go to `Editor > Manage Export Templates`.
2. If the export templates are not installed, click the **Download** button and follow the prompts to install them.

### Step 2: Configure Export Settings
1. Once the templates are installed, go to `Project > Export`.
2. Click the **Add...** button and choose **Web (HTML5)**.
   
### Step 3: Set HTML5 Export Options
1. In the `Export Preset` tab (for HTML5), you will see several options:
   - **HTML5** options include configuring the **canvas size**, **file compression**, and other settings. You can leave these as default unless you need specific configurations.
   
2. Optional settings you might consider:
   - **Custom HTML Shell**: If you want a custom HTML template, you can add it here.
   - **Compress Textures**: Compresses textures to make the game load faster.
   - **Minify JavaScript**: This option will reduce the file size of the JavaScript output.
   - **Framebuffer Allocation**: Leave it on the default unless you know your project has special requirements.

### Step 4: Export the Game
1. At the bottom of the Export window, you will see a **Destination** field. Choose the folder where you want to save the exported files.
2. Click the **Export Project** button.

This will generate an `index.html` file along with other necessary files (e.g., `.js`, `.wasm`, etc.).

### Step 5: Upload to a Web Server
Once exported, you can:
- Upload the files to a web server (e.g., GitHub Pages, itch.io, or your personal server).
- Open the `index.html` file locally using a web server (you may use something like Python's simple HTTP server to serve the game locally).

### Optional: Test Locally with a Simple HTTP Server
If you want to test the game locally:
1. **For Python users**, you can run a simple HTTP server:
   ```bash
   python3 -m http.server
   ```
2. Open a browser and go to `http://localhost:8000` to see your game in action.

Now your Godot game will be playable as an HTML5 web app!
