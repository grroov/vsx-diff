# Development & Packaging Guide

This guide explains how to set up, build, and package the **Antigravity Diff Folders** extension.

## 1. Prerequisites

Ensure you have [Node.js](https://nodejs.org/) (version 12 or higher) installed on your system.

## 2. Setup

Install the project dependencies using npm:

```bash
npm install
```

## 3. Building the Extension

The extension uses Gulp to handle the build process, which includes compiling TypeScript, processing SCSS, and generating the necessary assets.

```bash
# Compile and build everything (out/ and media/ directories)
npm run compile
```

To watch for changes and rebuild automatically during development:

```bash
npm run watch
```

## 4. Running Tests

The project includes a comprehensive test suite for the backend services.

```bash
npm test
```

## 5. Packaging (Creating a .vsix)

To package the extension for distribution on Open VSX or manual installation, you need the `vsce` CLI tool.

```bash
# Install vsce globally (if not already installed)
npm install -g @vscode/vsce

# Package the extension
vsce package
```

This will generate a file named `l13-diff-X.X.X.vsix` in the root directory.

## 6. Sideloading for Testing

To test the extension in **Antigravity** or **VS Code** without packaging it:

1.  Open the `vsx-diff` folder in your editor.
2.  Press `F5` (or go to **Run and Debug** -> **Extension**).
3.  A new **Extension Development Host** window will open with the extension active.

Alternatively, you can install the extension from the local directory:
*   Command Palette -> **Developer: Install Extension from Location...** -> Select this folder.
