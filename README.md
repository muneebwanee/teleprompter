# Teleprompter — Minimalist iOS & iPadOS Studio Teleprompter

**Teleprompter** (`v0.0.1`) is a fast, 100% offline teleprompter and camera app for **iPhone and iPad**, designed with a minimalist **Liquid Glass** interface, smooth vector motion graphics, front and back camera support, voice-synced scrolling, and Home Screen widgets.

Created by **[muneebwanee](https://github.com/muneebwanee)**.

---

## Features

- **Minimalist iOS & iPadOS Liquid Glass Design**
  - Switch effortlessly between **Dark Mode** and **Light Mode** with 6 studio color themes (*Orange*, *Gold*, *Red*, *Green*, *Blue*, and *Pure Black OLED*) and adjustable frosted glass blur.
  - Custom animated SVG vector art headers on script cards and a live 60fps harmonic wave ribbon that reacts to your reading speed.
- **Built-In Front & Back Camera Studio**
  - Switch between **Front Camera** and **Back Camera** (with `.5x`, `1x`, `2x`, and `3x` zoom controls) both inside the dedicated **Camera** tab and directly inside the full-screen **Reading Screen**.
  - Choose between a **Small Camera (PiP)** window or a **Full Camera Backdrop** behind your scrolling script, complete with a rule-of-thirds grid, `9:16` vertical video guide, and color filters.
- **Offline Voice Scroll & Listen Aloud**
  - **Follow Voice**: Automatically highlights words and scrolls your script as you speak, 100% offline on your device.
  - **Listen Aloud**: Hear your iPhone or iPad read your script out loud before you start recording.
  - **Short Lines**: Break long paragraphs into short, easy-to-read lines with one tap.
- **Reading Aids & Mirror Glass Support**
  - **Easy Read**: Bolds the start of each word so your eyes glide across sentences without losing your place.
  - **Flip Text (Left-Right / Up-Down)**: Mirrors the screen horizontally or vertically for physical teleprompter beam-splitter glass rigs.
  - **Auto-Wait on `[Pause]`**: Pauses scrolling for 2 seconds whenever a `[Pause]` tag reaches your reading line.
- **iOS & iPadOS Home Screen & Lock Screen Widgets**
  - Includes native `WidgetKit` widgets (`Small 2×2`, `Medium 4×2`, `Large 4×4`, and `Lock Screen`) to launch scripts or camera mode in one tap.
- **100% Offline & Private**
  - Every script, style preset, and setting stays on your device. No accounts, no cloud servers, and no tracking.

---

## Repository Structure

```text
teleprompter/
└── FlowPrompt_iOS_XcodeProject.zip
  ├── FlowPrompt.xcodeproj/                  # Universal iOS & iPadOS 16.0+ Xcode Project
  ├── project.yml                            # XcodeGen project specification
  ├── build_ipa.sh                           # Local macOS script to build unsigned .ipa
  ├── .github/workflows/build-ipa.yml        # GitHub Actions cloud .ipa builder & release publisher
  ├── FlowPrompt_Teleprompter_App.html       # Standalone offline iOS/iPadOS WebApp
  └── FlowPrompt/
    ├── Info.plist                         # Camera, Microphone, Speech, Photos & Bluetooth permissions
    ├── Assets.xcassets/AppIcon.appiconset # Universal iPhone & iPad App Icons (20pt–1024pt)
    ├── FlowPromptApp.swift                # App entry point
    ├── Models/
    │   ├── Script.swift                   # Script storage, reading time math & JSON backup
    │   ├── PresetStore.swift              # Quick-start camera & reading presets
    │   └── TeleprompterSettings.swift     # Real-time settings & Liquid Glass modifier
    ├── Services/
    │   ├── VoiceTrackEngine.swift         # On-device voice recognition & audio level sync
    │   └── CameraRecordingManager.swift   # Front & back AVCaptureSession camera manager
    ├── Views/
    │   ├── ContentView.swift              # Main navigation & script library
    │   ├── ScriptEditorView.swift         # Script editor, Listen Aloud & cue bar
    │   ├── BroadcastCameraView.swift      # Built-in iOS camera & floating script box
    │   ├── TeleprompterView.swift         # Full-screen reading stage, Front/Back cam & Mirror X/Y
    │   ├── VectorMotionArtView.swift      # 60fps SwiftUI Canvas vector wave graphics
    │   └── SettingsDrawerView.swift       # Settings, App Access, Privacy Policy, Terms & About
    └── FlowPromptWidgets/
        └── FlowPromptWidgetBundle.swift   # Home Screen & Lock Screen WidgetKit extension
```

---

## Installation & Sideloading

### Option 1 — Download Pre-Built `.ipa` from GitHub Releases (iPad / iPhone)

1. Go to the **[Releases](../../releases)** page of this repository.
2. Download **`FlowPrompt_iOS_XcodeProject.ipa`** from the latest `FlowPrompt_iOS_XcodeProject` release.
3. Install the `.ipa` on your iPad or iPhone using:
   - **SideStore / AltStore / Feather** (On-device, no computer required)
   - **Sideloadly** (Windows / macOS)

### Option 2 — Build `.ipa` Automatically on GitHub Actions

1. Fork or push this repository to your GitHub account.
2. Open the **Actions** tab and run the **Build Unsigned Teleprompter iOS IPA** workflow.
3. GitHub Actions compiles the app on `macos-14`, generates and embeds all iPhone and iPad `AppIcon` sizes via `xcrun actool`, and publishes `FlowPrompt_iOS_XcodeProject.ipa` directly to **Releases**.

### Option 3 — Build Locally with Xcode (macOS)

```bash
git clone [https://github.com/muneeb/teleprompter.git](https://github.com/muneeb/teleprompter.git)
cd teleprompter
chmod +x build_ipa.sh
./build_ipa.sh
```
Or open `FlowPrompt.xcodeproj` in **Xcode 15+**, select your Apple ID under **Signing & Capabilities**, and press **`Cmd + R`** to run on your connected iPhone or iPad.

### Option 4 — Instant Standalone Home-Screen App (No Sideloading Needed)

1. Open **`FlowPrompt_Teleprompter_App.html`** in **Safari** on your iPad or iPhone.
2. Tap **Share → Add to Home Screen**.
3. Launch **Teleprompter** from your Home Screen with its custom app icon and full-screen offline interface.

---

## Keyboard & Bluetooth Remote Shortcuts

| Action | Key / Pedal |
| :--- | :--- |
| **Start / Pause Reading** | `Space` / `Enter` |
| **Faster Speed (+5 WPM)** | `Up Arrow` |
| **Slower Speed (-5 WPM)** | `Down Arrow` |
| **Flip Text Left-Right** | `M` |
| **Exit Reading Screen** | `Esc` |

---

## Privacy & License

- **100% On-Device Privacy**: All scripts, settings, and camera/microphone streams are processed locally on your device.
- **Author**: **[muneebwanee](https://github.com/muneebwanee)**
- **License**: Released under the [MIT License](LICENSE).
