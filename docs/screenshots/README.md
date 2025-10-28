# Screenshots

This directory contains interface screenshots for demo purposes.

## Instructions for Adding Screenshots

### What to Capture

1. **Main Interface** (`01-main-interface.png`)
   - Full Gradio interface
   - Summarize tab visible
   - Model selector showing options
   - Text input area with sample text

2. **Generation in Progress** (`02-generating.png`)
   - Status showing "Generating summary..."
   - Progress indicator

3. **Summary Results** (`03-summary-results.png`)
   - Generated summary displayed
   - Statistics panel visible
   - Compression ratio shown
   - Processing time displayed

4. **Export Tab** (`04-export-options.png`)
   - Export tab active
   - All 4 export format buttons visible
   - Status messages

5. **Export Success** (`05-export-success.png`)
   - File download link visible
   - Success message shown
   - Exported file ready for download

6. **Help Tab** (`06-help-tab.png`)
   - Help documentation visible
   - Usage instructions shown

### How to Capture

**On Windows**:
- Press `Win + Shift + S` for Snipping Tool
- Or use `Win + PrtScn` for full screen

**On macOS**:
- Press `Cmd + Shift + 4` for selection
- Or `Cmd + Shift + 3` for full screen

**On Linux**:
- Use Screenshot tool (varies by distro)
- Or install `gnome-screenshot`

### Recommended Resolution

- **Resolution**: 1920x1080 or higher
- **Format**: PNG (best quality)
- **File Size**: Keep under 500KB each
- **Compression**: Use TinyPNG or similar if needed

## Naming Convention

```
[sequence]-[description]-[optional-detail].png

Examples:
01-main-interface.png
02-generating-summary.png
03-summary-results-bart.png
04-export-tab.png
05-markdown-download.png
```

## Alternative: Demo Video

Instead of screenshots, consider recording a demo video:

### Tools
- **Loom** (free, 5 min limit): https://loom.com
- **OBS Studio** (free, unlimited): https://obsproject.com
- **ScreenToGif** (Windows, animated GIFs): https://www.screentogif.com

### Video Script (2-3 minutes)

1. **Intro** (10 sec)
   - "Hi, this is my Day 2 AI Engineering Bootcamp project"
   - "Text summarization with multi-format export"

2. **Demo** (90 sec)
   - Paste sample text
   - Select model (T5 Small)
   - Click generate
   - Show results and statistics
   - Navigate to Export tab
   - Export to Markdown, JSON
   - Show downloaded files

3. **Code Explanation** (30 sec)
   - Quick walkthrough of architecture
   - Highlight key components (ModelManager, CacheManager)

4. **Outro** (10 sec)
   - "Thanks for watching!"
   - Show GitHub link

### Hosting Demo Video

After recording:
- Upload to YouTube (unlisted)
- Upload to Loom
- Create `demo-video-link.md` in this directory

## Example demo-video-link.md

```markdown
# Demo Video

Watch the complete demo here: [YouTube Link](https://youtube.com/watch?v=...)

**Duration**: 2:45
**Topics Covered**:
- Interface walkthrough
- Model comparison
- Export functionality
- Code architecture
```

---

**For Bootcamp Submission**: Include at least 3-4 screenshots OR a 2-3 minute demo video.
