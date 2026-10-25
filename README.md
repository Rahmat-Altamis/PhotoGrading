# PhotoGrading

Hello everyone, good morning/afternoon/evening! So, what is PhotoGrading? Well, let me tell a story first. A few years ago, when I was still a child, I loved photography, but I was too lazy to pick the best photos one by one. Well, that was 5 years ago, and now we have AI. NICE! What if AI could rate photos and help me choose their best use? That's why I'm building this.

## App Demo

![PhotoGrading preview](image.png)

[Watch the demo video](./demo.webm)

## Installation

I'm currently using Arch Linux, and I'm too lazy to run a VM just to compile separate Windows and Debian packages. So, I built the application as an AppImage, which is pretty convenient.

### Linux (AppImage)

1. Download the AppImage from [GitHub Releases](https://github.com/Rahmat-Altamis/PhotoGrading/releases/tag/V1.0.0.0).
2. Open a terminal in the directory where you downloaded the file.
3. Make the AppImage executable and run it:

   ```bash
   chmod +x ImageRater-x86_64.AppImage
   ./ImageRater-x86_64.AppImage
   ```

   If the downloaded file has a different name, replace `ImageRater-x86_64.AppImage` with its actual filename.

**Alternative: Using the file manager**

Right-click the downloaded AppImage, open **Properties → Permissions**, enable **Allow executing file as program**, then double-click the file to launch it. The exact permission option may vary depending on your Linux desktop environment.

### Using the application

1. Enter your Hack Club AI API key in the application.
2. Select the folder containing the photos you want to sort.
3. Press **Grade It**.
4. Wait for the results.
5. The application may also recommend renaming your photos. Press **Yes** to rename them using the suggested grade, edit recommendations, and theme.

### Running from source

If you prefer to clone the repository and run the application yourself:

1. Clone the repository:

   ```bash
   git clone https://github.com/Rahmat-Altamis/ImageRater.git
   cd ImageRater
   ```

2. Run the setup script for your operating system.

   **Windows:** Run `run.bat`.

   **Linux:**

   ```bash
   chmod +x run.sh
   ./run.sh
   ```

   These scripts set up the Python environment, install the required dependencies, and launch the application.

3. When the GUI opens, enter your API key, configure the passing grades, and adjust the other settings.
4. You're done!

## Catalog

Here's the catalog of classification codes, so you won't be confused when editing your photos.

### Uses

- `1`: Worth posting to social media
- `2`: Worth selling
- `3`: Worth entering in a competition
- `0`: NOT worth any of the three (every score is below its threshold)

### Worth Bars

- `1`: 6
- `2`: 7
- `3`: 8

### Themes

- `a`: abstract — deliberate abstract art or graphics ONLY; never for blurry or unclear photos
- `b`: product — products, objects, still life
- `c`: city — buildings, architecture, and streets where the place is the subject
- `f`: food — food and drinks
- `l`: landscape — scenery, sky, roads, and outdoor views with no main person or vehicle
- `m`: vehicle — cars, motorcycles, racing, and panning shots of moving vehicles (even if blurry)
- `n`: nature — plants, flowers, trees
- `p`: people — portraits, groups, and candid photos of people
- `s`: sport — sports and action (non-motor)
- `w`: animal — wildlife, pets, and other animals
- `x`: other — screenshots, documents, or anything that fits nothing else

### Edits

- `+`: exposure — fix exposure or brightness
- `~`: color — fix color or white balance
- `#`: sharpen — sharpen or reduce noise
- `^`: crop — crop, straighten, or recompose
- `@`: retouch — remove distractions or retouch
- `!`: reshoot — major problems; reshoot if possible
- `=`: none — no edit needed
- `%`: unclear — edit advice unclear (the AI gave no usable answer)

### Edit Hints

- `crop|rotate|straighten|tilt|orient|frame|compos`: `^`
- `exposure|bright|underexpose|overexpose|shadows|highlights`: `+`
- `white balance|colour|saturate|tint`: `~`
- `sharpen|noise|grain|soft`: `#`
- `retouch|distract|clone|erase|remove`: `@`
- `reshoot|retake|unusable`: `!`

## Features

- Grade your photos for their best use, theme, and suggested edits
- Set the minimum passing grade for each style in the app UI
- Change the grading and judge models
- Enable or disable the judge
- Re-rate photos
- Check subfolders
- View the classification legends in the app without needing to open this README

## Tech Stack

### Language

- Python

### GUI

- PySide6 (Qt for Python)
  - `QWidget`
  - `QTableWidget`
  - `QThread`

### AI / API

- Hack Club AI
- OpenAI-compatible `/chat/completions` endpoint with base64 image input
- Grader model: `google/gemini-2.5-flash`
- Judge model: `z-ai/glm-5.3-flash`

## Dependencies

The Python dependencies are listed in [`requirements.txt`](./requirements.txt). The setup scripts install the required packages and prepare the environment.

Python must be installed to run the application from source. The AppImage is intended for Linux users who want to run the packaged application without manually installing the Python dependencies.

## License

This project is licensed under the MIT License. See [`LICENSE`](./LICENSE) for the full license text.
