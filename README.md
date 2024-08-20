
<p align="center">
<h1 align="center">FlowVision</h1>
<h3 align="center">Waterfall-style Image Viewer for macOS<br><br><a href="./README_zh.md">[中文说明]</a></h3> 
</p>

[![](https://img.shields.io/github/release/netdcy/FlowVision.svg)](https://github.com/netdcy/FlowVision/releases/latest?color=blue "GitHub release") ![GitHub License](https://img.shields.io/github/license/netdcy/FlowVision?color=blue)


## Screenshots

![preview](https://netdcy.github.io/FlowVision/docs/preview.jpg)

## Features:
 - Adaptive layout mode, light/dark mode
 - Convenient file management (similar to Finder)
 - Right-click gestures, quickly find the previous/next folder with images/videos
 - Performance optimizations for directories with a large number of images
 - High-quality scaling (reduces moiré and other issues)
 - Support for video thumbnails
 - Recursive mode

## Installation and Usage

### System Requirements

 - macOS 11.0 and Later

### Privacy and Security

 - Open source
 - No Internet connection
 - Provide unsigned official builds

### Homebrew Install

 ```
brew tap netdcy/flowvision
brew install flowvision --no-quarantine
 ```

## Instructions:
### In Image View:
 - Double-click to open/close the image. 
 - Hold down the right/left mouse button and scroll the wheel to zoom
 - Hold down the middle mouse button and drag to move the window
 - Long press the left mouse button to switch to 100% zoom
 - Long press the right mouse button to fit the image to the view
### Right-Click Gestures:
 - Right/Left: Switch to the next/previous folder with images/videos (logically equivalent to the next folder when sorting all folders on the disk)
 - Up: Switch to the parent directory
 - Down: Return to the previous directory
 - Down-Right/Down-Left: Switch to the next/previous folder with images at the same level as the current folder
 - Up-Right/Up-Left: Switch to the parent directory, then perform the Down-Right/Down-Left action
### Keyboard Shortcuts:
 - W: Same as the right-click gesture Up
 - A/D: Same as the right-click gesture Left/Right
 - S: Same as the right-click gesture Down

## FAQ

**Q1: Why can't I open the application? I see a warning saying the app is not trusted.**

**A1:** This happens because the app is not notarized by Apple. To open it:
- Find the app in the Finder.
- Right-click the app file.
- Select "Open" from the menu.
- Click "Open" in the dialog that appears.

(ref: https://support.apple.com/102445#openanyway)

**Q2: Why isn't the application notarized?**

**A2:** Notarizing an app requires an annual $100 fee to Apple. To keep the software free, we haven't notarized it. If you prefer, you can build the app yourself from the source code.

**Q3: Why doesn't the application have an auto-update feature?**

**A3:** Checking for updates requires a network connection, and the philosophy of this project is to ensure that data privacy remains entirely under the user's control. Using auto-update could lead to scenarios where the developer's account is compromised, and malicious code is distributed through the update channel. To ensure the safety and privacy of your data, we have chosen not to include an auto-update feature.

## Build

### Environment

Xcode 15.2+

### Libraries

 - https://github.com/arthenica/ffmpeg-kit
 - https://github.com/attaswift/BTree
 - https://github.com/sindresorhus/Settings

### Steps

1. Clone the source code of the project and libraries.
2. For ffmpeg-kit, it need to be built to binary first. If you want to save time, you can directly download its pre-built binary, named like `ffmpeg-kit-full-gpl-6.0-macos-xcframework.zip` (not LTS version). Unzip it, then execute this in terminal to remove its quarantine attribute:

    ```
    sudo xattr -rd com.apple.quarantine ./ffmpeg-kit-full-gpl-6.0-macos-xcframework
    ```

3. Organize the directory structure as shown below:

    ```
    ├── FlowVision
    │   ├── FlowVision.xcodeproj
    │   └── FlowVision
    │       └── Sources
    ├── ffmpeg-kit-build
    │   └── bundle-apple-xcframework-macos
    │       ├── ffmpegkit.xcframework
    │       └── ...
    ├── BTree
    │   ├── Package.swift
    │   └── Sources
    └── Settings
        ├── Package.swift
        └── Sources
    ```

4. Open `FlowVision.xcodeproj` by Xcode, click 'Product' -> 'Build For' -> 'Profiling' in menu bar.
5. Then 'Product' -> 'Show Build Folder in Finder', and you will find the app is at `Products/Release/FlowVison.app`.

## License

This project is licensed under the GPL License. See the [LICENSE](https://github.com/netdcy/FlowVision/blob/main/LICENSE) file for the full license text.
