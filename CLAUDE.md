# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Josh Chou's Interactive Portfolio - a unique 3D web-based portfolio built as a single HTML file with embedded Three.js. The portfolio presents a virtual office environment where visitors can explore, interact with Josh's character, view gallery images, and learn about his professional background.

## Architecture

### Core Structure
- **Single HTML File**: `port.html` contains the entire application
- **No Build System**: Direct HTML/CSS/JavaScript implementation with CDN dependencies
- **Three.js Integration**: Uses Three.js r128 for 3D rendering and scene management

### Key Components

1. **3D Scene Management** (lines 504-663)
   - Camera setup with first-person perspective
   - Lighting system with ambient and directional lights
   - Environment creation (floor, walls, ceiling with materials)

2. **Interactive Gallery System** (lines 813-1132)
   - Dynamic painting placement around virtual walls
   - Image loading with fallback to placeholder content
   - Gallery content mapping for 9 paintings with local image sources

3. **Character System** (lines 1158-1274)
   - 3D character creation with customizable appearance
   - Josh Chou character with biographical data
   - Character AI with movement patterns and animations

4. **Dialogue System** (lines 1490-1791)
   - Interview/recruitment-focused conversation system
   - Predefined responses covering professional background
   - Custom question input with dynamic response generation

5. **Player Controls** (lines 1348-1411)
   - WASD movement with collision detection
   - Arrow key/mouse camera rotation (horizontal only)
   - Space bar jumping mechanics
   - Pointer lock for immersive control

6. **UI Overlay Systems**
   - Contact modal with professional links
   - Social media integration
   - Painting tooltips on proximity
   - Instruction overlay for controls

### Media Assets
The portfolio uses local image files served from the same directory:
- Professional photos (DSCF5164.jpg, DSCF6482.jpg, etc.)
- Personal photos (IMG_*.jpeg/JPG)
- Resume PDF (JoshChouResume.pdf)

### Development Workflow

**Running the Portfolio:**
```bash
# Start a local server to serve images
python -m http.server 8000
# OR
npx serve .
# Then open port.html in browser
```

**Image Management:**
- Images are referenced with localhost URLs in the gallery content
- Fallback "Portfolio Image" placeholders for missing content
- All images should be placed in the root directory

**Content Updates:**
- Gallery content is defined in the `galleryContent` object (lines 907-962)
- Josh's responses are in the `generateJoshResponse` function (lines 1669-1759)
- Painting tooltips are in the `paintingTooltips` object (lines 1848-1885)

### Technical Features

- **Collision Detection**: Prevents walking through furniture and objects
- **Physics System**: Basic gravity and jumping mechanics
- **Responsive Design**: Adapts to different screen sizes
- **Cross-browser Compatibility**: Uses standard web APIs and CDN resources
- **Performance Optimization**: Efficient rendering with shadow mapping and fog

### Content Customization

To update portfolio content:
1. **Gallery Images**: Replace image files and update `galleryContent` object
2. **Character Responses**: Modify response arrays in `generateJoshResponse`
3. **Contact Information**: Update social links and email addresses
4. **Visual Styling**: Modify CSS variables and Three.js materials

## Development Notes

- No package.json or build tools required
- All dependencies loaded via CDN (Three.js r128)
- Self-contained architecture enables easy deployment
- Local server required for image loading due to CORS restrictions
- Images currently use localhost URLs and need updating for production deployment