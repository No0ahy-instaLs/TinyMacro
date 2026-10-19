# TinyMacro

TinyMacro is a beginner-friendly Windows desktop macro recorder built with Python, PySide6, and pynput.

## Features in this first version

- Records mouse movement, clicks, scrolling, and keyboard press/release events.
- Replays actions with timing, speed adjustment, pause/resume, repeat count, or infinite looping.
- Editable action table (double-click delay and coordinate cells).
- Save and open JSON-based `.tmacro.json` files.
- Global shortcuts: `Ctrl+Alt+R` record/stop recording, `Ctrl+Alt+P` play, `Ctrl+Alt+S` stop playback.
- Dark UI.

## 1. Install Python

Install Python 3.11 or 3.12 from https://www.python.org/downloads/windows/.
During setup, check **Add python.exe to PATH**.

## 2. Open the project folder

Extract the ZIP, open the `TinyMacro` folder in File Explorer, click the address bar, type `cmd`, and press Enter.

## 3. Create a virtual environment and install dependencies

Run these commands in Command Prompt:

```bat
py -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

## 4. Run TinyMacro

```bat
python tinymacro.py
```

## 5. Build a standalone EXE

From the same activated Command Prompt:

```bat
pyinstaller --noconfirm --clean --windowed --name TinyMacro --collect-all pynput tinymacro.py
```

When it finishes, the app will be here:

`dist\TinyMacro\TinyMacro.exe`

This command creates a folder-based distribution, which is generally more reliable for input-hook libraries than a single-file EXE. You can share the entire `dist\TinyMacro` folder. If you later add an icon, use `--icon app.ico`.

## Important safety notes

- Test macros in a harmless app first. Playback sends real keyboard and mouse input to whatever window has focus.
- Stop playback before using your computer normally. `Ctrl+Alt+S` is the global stop shortcut.
- Infinite loops keep running until stopped.
- Some elevated/admin applications may not accept input from a non-elevated TinyMacro process.
- Antivirus may scrutinize newly packaged automation executables; distribute only builds you made yourself.
- This version does not include image recognition or AI automation yet. Those are good next milestones.
