# Teleprompter — Minimalist iOS & iPadOS Studio Teleprompter, Camera & Video Trimmer

**Teleprompter** (`v0.0.1`) is a fast, 100% offline teleprompter, camera studio, and post-capture video trimmer app for **iPhone and iPad**, built with a minimalist **Liquid Glass** interface, 60fps vector motion graphics, front and back camera recording, interactive micro-controls, voice-synced scrolling, and selectable Home Screen & Lock Screen widgets.

Created by **[muneebwanee](https://github.com/muneebwanee)**.

## Features

- **Minimalist iOS & iPadOS Liquid Glass Design**
  - Switch in real time between **Dark Mode** and **Light Mode** with 6 live studio color themes (*Orange*, *Gold*, *Red*, *Green*, *Blue*, and *Pure Black*) that animate across every screen.
  - Custom animated SVG vector art headers on script cards, custom glassmorphic studio icons, and a live 60fps harmonic wave ribbon that responds to your reading speed.
- **Built-In Front & Back Camera Studio**
  - Hardware-backed `AVCaptureVideoPreviewLayer` viewfinder (`PreviewVideoView`) that displays your live camera feed immediately upon granting permission.
  - Switch between **Front Camera** and **Back Camera** (`1x`, `2x`, `3x` zoom) both inside the dedicated **Camera** studio and directly inside the full-screen **Reading Screen**.
  - Choose between a **Small Camera (PiP)** window near the top lens or a **Full-Screen Camera Backdrop** behind your scrolling script.
- **Post-Capture Video Editor & Trimmer**
  - Stopping a recording automatically opens the built-in **Video Editor & Trimmer** (`VideoClipEditorView`), where you can preview your take, drag **Start Trim** and **End Trim** sliders with live frame seeking, export a lossless trimmed clip on-device (`AVAssetExportSession`), adjust playback speed (`0.5x`–`2x`), **Save to Photos**, **Save to Files**, or **Share**.
- **Selectable Home Screen & Lock Screen Widgets + Interactive Jiggle Mode**
  - Includes 4 native `WidgetKit` widgets (`TeleprompterWidgetBundle.swift`): **Quick Script Launcher (`2×2` & `4×2`)**, **Dual Camera & Mirror Rig (`2×2` & `4×2`)**, **Speaking Pace & Goal Rings (`2×2` & Lock Screen Circular)**, and **Live Script Reader (`4×4`)**.
  - Inside the app's **Widgets** tab (`WidgetsGalleryView.swift`), tap **Edit Home Screen / Edit Widgets** to enter interactive **Jiggle Mode** and customize your active widgets, or use the **Interactive Rotary WPM Speed Dial** and draggable **Eye-Line & Mirror Calibrator**.
- **Interactive Reading Modes & Voice Scroll**
  - Switch anytime between **Smooth Speed**, **Follow Voice** (on-device speech recognition), **Sound Trigger**, and **Manual Touch** using the always-visible bottom mode pill bar.
  - **Listen Aloud**: Hear your iPhone or iPad read your script out loud before filming.
  - **Short Lines**: Break long paragraphs into short, easy-to-read teleprompter lines with one tap.
- **100% Offline & Private**
  - Every script, video clip, and setting stays on your device. No accounts, no cloud servers, and no tracking.

## Repository Structure

```text
teleprompter/
├── Teleprompter.xcodeproj/                # Universal iOS & iPadOS 16.0+ Xcode Project (Format 56)
├── project.yml                            # XcodeGen project specification
├── build_ipa.sh                           # Local macOS script to build unsigned .ipa
├── .github/workflows/build-ipa.yml        # GitHub Actions cloud .ipa builder & release publisher
├── Teleprompter_App.html                  # Standalone offline iOS/iPadOS WebApp
└── Teleprompter/
    ├── Info.plist                         # Camera, Microphone, Speech, Photos & Bluetooth permissions
    ├── Assets.xcassets/AppIcon.appiconset # Universal iPhone & iPad App Icons (20pt–1024pt)
    ├── TeleprompterApp.swift              # App entry point & live theme environment
    ├── Models/
    │   ├── Script.swift                   # Script storage, reading time math & Short Lines formatter
    │   ├── PresetStore.swift              # Quick-start camera & reading presets
    │   └── TeleprompterSettings.swift     # Real-time 6-Theme engine, Dark/Light mode & Liquid Glass
    ├── Services/
    │   ├── VoiceTrackEngine.swift         # On-device voice recognition, audio level & Listen Aloud
    │   └── CameraRecordingManager.swift   # Live AVCaptureVideoPreviewLayer & video trimming engine
    ├── Views/
    │   ├── ContentView.swift              # Main navigation, vector wave header & script library
    │   ├── ScriptEditorView.swift         # Script editor, Listen Aloud, Short Lines & cue bar
    │   ├── BroadcastCameraView.swift      # Built-in iOS camera & floating script overlay
    │   ├── TeleprompterView.swift         # Full-screen reading stage, Mode bar & Front/Back camera
    │   ├── VideoClipEditorView.swift      # Post-capture video editor, trimmer, Save to Photos & Files
    │   ├── WidgetsGalleryView.swift       # Interactive Home Screen Widget Jiggle Mode & Rotary Speed Dial
    │   ├── VectorMotionArtView.swift      # 60fps SwiftUI Canvas vector wave graphics
    │   └── SettingsDrawerView.swift       # Animated Liquid Glass Settings, Privacy, Terms & About
    └── TeleprompterWidgets/
        └── TeleprompterWidgetBundle.swift # Home Screen & Lock Screen WidgetKit bundle (4 widgets)
```

## Installation & Sideloading

### Option 1 — Download Pre-Built `.ipa` from GitHub Releases (iPad / iPhone)

1. Go to the **[Releases](../../releases)** page of this repository.
2. Download **`Teleprompter-iOS-Universal.ipa`** from the latest `v0.0.1` release.
3. Install the `.ipa` on your iPad or iPhone using **SideStore**, **AltStore**, **Feather**, or **Sideloadly**.

### Option 2 — Build `.ipa` Automatically on GitHub Actions

1. Upload `Teleprompter_iOS_XcodeProject.zip` to your repository and add `.github/workflows/build-ipa.yml`.
2. Open the **Actions** tab and run **Build Unsigned Teleprompter iOS IPA**.
3. GitHub Actions compiles the app on `macos-14`, embeds all 18 iPhone and iPad `AppIcon` sizes via `xcrun actool`, and publishes `Teleprompter-iOS-Universal.ipa` directly to **Releases**.

### Option 3 — Build Locally with Xcode (macOS)

```bash
git clone [https://github.com/muneeb/teleprompter.git](https://github.com/muneeb/teleprompter.git)
cd teleprompter
chmod +x build_ipa.sh
./build_ipa.sh
```

### Option 4 — Instant Standalone Home-Screen App (No Sideloading Needed)

1. Open **`Teleprompter_App.html`** in **Safari** on your iPad or iPhone.
2. Tap **Share → Add to Home Screen** to launch **Teleprompter** full-screen with its custom icon.

## Keyboard & Bluetooth Remote Shortcuts

| Action | Key / Pedal |
| :--- | :--- |
| **Start / Pause Reading** | `Space` / `Enter` |
| **Faster Speed (+5 WPM)** | `Up Arrow` |
| **Slower Speed (-5 WPM)** | `Down Arrow` |
| **Flip Text Left-Right** | `M` |
| **Exit Reading Screen** | `Esc` |

## Privacy & License

- **100% On-Device Privacy**: All scripts, settings, and camera/microphone recordings stay on your device.
- **Author**: **[muneebwanee](https://github.com/muneebwanee)**
- **License**: Released under the [MIT License](LICENSE).
