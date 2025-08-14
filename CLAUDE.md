# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a zero-dependency A/B audio player built with vanilla HTML, CSS, and JavaScript. It allows users to toggle between two versions of the same audio file for side-by-side comparison (useful for audio mixing/production comparison).

## Architecture

### Core Files
- `index.html` - Main HTML page with two audio player instances
- `js/ab-player.js` - Core JavaScript functionality for audio playback and controls
- `css/style.css` - Styling (currently mostly commented out from recent style removal)
- `assets/` - Audio files (sound1-a.mp3, sound1-b.mp3, sound2-a.mp3, sound2-b.mp3)

### Key Components
- **Player Wrapper**: Each `.player__wrapper` div represents one A/B player instance with `data-audio-a` and `data-audio-b` attributes
- **Audio Elements**: Dynamically created audio elements for each sound pair
- **Progress Bar**: Interactive progress bar for seeking and visual feedback
- **A/B Controls**: Toggle buttons to switch between audio versions
- **Play/Stop Controls**: Standard media controls

### JavaScript Architecture
- `initializePlayers()` function processes each `.player__wrapper` element
- Audio loading handled via `canplaythrough` events with readiness flags
- Cross-player synchronization prevents multiple players from playing simultaneously
- Progress tracking using `requestAnimationFrame` for smooth updates
- Mobile detection for audio playback compatibility

## Development

### No Build Process
This is a vanilla JavaScript project with no build tools, package managers, or dependencies. Development is done directly by editing the source files.

### Testing
Open `index.html` directly in a web browser. The demo is also available at: https://mattbartley.github.io/AB-Audio-Player/

### File Structure
```
/
├── index.html          # Main demo page
├── ssindex.html        # Alternative version with external asset URLs
├── js/ab-player.js     # Core functionality
├── css/style.css       # Styling (mostly commented out)
├── assets/             # Audio files directory
└── favicon files       # Various icon formats
```

## Usage Notes

### Adding New Players
To add audio pairs, create new `.player__wrapper` divs in the HTML with `data-audio-a` and `data-audio-b` attributes pointing to the audio files.

### Audio Requirements
- Audio files must have the same duration to work correctly
- Supported formats: MP3, WAV, OGG (browser-dependent)
- Files should be placed in the `assets/` directory

### Browser Compatibility
- Mobile detection is implemented for audio playback without user gesture requirements
- Different browsers handle audio preloading differently - test thoroughly for production use