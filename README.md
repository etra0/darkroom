# Darkroom Timer (OLED Safe)

A pure single-file web application (`index.html`) designed specifically for darkroom photographic printing and film processing on OLED displays.

## Key Features

- **Strict OLED & Safelight Protection**:
  - Background is true `#000000`, turning off OLED subpixels completely (0 nits emitted).
  - Absolutely **zero white, blue, or green light**. Every text element, button, border, and focus outline is rendered in deep photographic red wavelengths (~630–660nm).
  - Includes a red intensity / dimming slider for papers sensitive to high light levels.
- **Stage Progression with Manual "Continue"**:
  - Three stages: **1. Develop**, **2. Stop Bath**, and **3. Fixer**.
  - When a stage finishes, the timer alerts you (haptic vibration, safe chime, red pulse), **automatically advances to the next stage**, but **waits for you to manually press `CONTINUE`** (or press Spacebar) before starting the countdown.
  - When **Fixer** finishes, it automatically loops back to **Develop** and increments the print cycle counter (`Cycle: #1`, `#2`, etc.).
- **Optimized for Both Phones and Wide Screens**:
  - **Phone / Portrait**: Compact single-column view with giant touch targets, thumb-friendly buttons, and responsive circular progress dial.
  - **Wide Screens / Tablets / Desktop**: Adaptive 2-column widescreen layout with an oversized dial and numbers legible across the room, vertical stage progress track, and desktop keyboard shortcuts.
  - **Horizontal Phone / Landscape**: Height-adaptive compact landscape mode so nothing is cut off.
- **Hands-Free / Keyboard Shortcuts** (Great for desktops & laptops across the sink):
  - <kbd>Space</kbd>: Start / Pause / Continue
  - <kbd>R</kbd>: Reset current stage
  - <kbd>N</kbd> or <kbd>→</kbd>: Skip to next stage
  - <kbd>F</kbd>: Toggle Fullscreen
  - <kbd>S</kbd>: Open Settings
- **Fullscreen & Wake Lock**:
  - Requests Fullscreen mode on start to prevent notification banners and navigation bars.
  - Employs the **Screen Wake Lock API** (`navigator.wakeLock`) so the screen never sleeps or locks during darkroom sessions.
- **Vibration Alert**:
  - Fires a distinct triple-pulse vibration pattern (`[600, 200, 600, 200, 800]`) when each stage completes.
- **Persistent Memory**:
  - Saves your custom durations (minutes and seconds) and preferences into `localStorage`.
- **Zero Dependencies**:
  - Fully self-contained in [index.html](file:///Users/saedo/Documents/work/darkroom/index.html). Works 100% offline and in Airplane Mode once loaded.

## How to Deploy to GitHub Pages

1. In your darkroom directory:
   ```bash
   git init
   git add .
   git commit -m "Darkroom timer with manual continue and responsive layout"
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git branch -M main
   git push -u origin main
   ```
2. In your GitHub repository:
   - Go to **Settings** → **Pages**.
   - Under **Build and deployment** > **Source**, choose **Deploy from a branch**.
   - Select the `main` branch and `/ (root)` folder, then click **Save**.
3. Your darkroom timer will be live at `https://<your-username>.github.io/<repo-name>/`.
