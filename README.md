# Space Time AR - Setup Instructions

## Files Needed for GitHub Deployment

Your repository should contain:
1. `index.html` - The main AR application file
2. `heromarketer2.png` - Your marker image
3. `heromarketer2.patt` - The marker pattern file (generated from the PNG)

## How to Generate the Marker Pattern File

AR.js requires a `.patt` pattern file generated from your marker image. Follow these steps:

### Method 1: Use the AR.js Marker Training Tool (Recommended)

1. Go to: https://ar-js-org.github.io/AR.js/three.js/examples/marker-training/examples/generator.html

2. Upload your `heromarketer2.png` file

3. Click "Download Marker" - this will download `pattern-heromarketer2.patt`

4. Rename the downloaded file to `heromarketer2.patt`

5. Place `heromarketer2.patt` in your GitHub repository root alongside `index.html`

### Method 2: Use the Online Pattern Generator

1. Go to: https://jeromeetienne.github.io/AR.js/three.js/examples/marker-training/examples/generator.html

2. Click "Upload Image" and select `heromarketer2.png`

3. Download the generated pattern file

4. Rename it to `heromarketer2.patt`

5. Upload to your GitHub repository

## GitHub Pages Deployment

1. Upload these files to your GitHub repository:
   - `index.html`
   - `heromarketer2.png`
   - `heromarketer2.patt`

2. Go to your repository Settings → Pages

3. Under "Source", select the branch (usually `main`) and root folder

4. Click "Save"

5. Your AR experience will be available at: `https://[username].github.io/[repository-name]/`

## How to Use

1. Print `heromarketer2.png` on A4 paper (color or black & white)

2. Open the deployed URL on a mobile device with camera

3. Click "activate camera" and grant camera permissions

4. Point the camera at the printed marker

5. The 3D shapes will appear anchored to the marker with the following pattern:
   - **Shape 1**: Comes toward center, then arcs to the RIGHT
   - **Shape 2**: Comes toward center, then arcs to the LEFT  
   - **Shape 3**: Comes toward center and FILLS THE SCREEN (stays centered)
   - Pattern repeats for shapes 4-6

## Audio

Audio should work through device speakers (not just headphones). You'll hear:
- A brief diagnostic beep when starting (confirms audio is working)
- Ambient drone background throughout
- Individual tones for each shape that vary based on animation progress

## Troubleshooting

**Marker not detected:**
- Ensure good lighting (avoid shadows on the marker)
- Make sure the marker is flat and fully visible
- Try moving the camera closer or farther from the marker
- Marker size: A4 works well; smaller markers may be harder to detect

**No audio on device speakers:**
- Check device volume settings
- Some browsers require user interaction before playing audio - the "activate camera" button handles this
- Try refreshing the page and clicking the button again

**Shapes appear at wrong position:**
- Verify `heromarketer2.patt` file is in the same directory as `index.html`
- Check browser console for errors
- Ensure the pattern file matches the marker image

## File Structure

```
your-repository/
├── index.html
├── heromarketer2.png
├── heromarketer2.patt
└── README.md (this file)
```

## Technical Details

**Trajectory Pattern (repeating every 3 shapes):**
1. Right arc: Emanates from marker → approaches center → arcs right off-screen
2. Left arc: Emanates from marker → approaches center → arcs left off-screen
3. Center fill: Emanates from marker → approaches very close → fills screen → exits

**Audio Enhancements:**
- Limiter threshold: -1dB (optimized for speakers)
- Drone volume: 0.20 (increased from 0.12)
- Shape sound peak: 0.45 (increased from 0.28)
- Explicit AudioContext resume for iOS/Safari compatibility

**Libraries Used:**
- A-Frame 1.2.0
- AR.js (marker-based tracking)
- Three.js r128
