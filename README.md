# Recorder Android

Minimal Android voice recorder that saves clean, speech-ready WAV files. Standalone app
extracted from `transcriber-android` (see [omniAI](https://github.com/nano-rex/omniAI)).

## Features
- start and stop microphone recording
- prefer Android `VOICE_RECOGNITION` input, with `MIC` fallback
- enable supported speech audio effects when available
- save enhanced 16 kHz mono WAV files locally
- choose the recording source and a workspace folder; play back the latest file
- dark mode

## Build

Requirements: JDK 17 and the Android SDK with platform 34 and build-tools 34
(`sdkmanager "platforms;android-34" "build-tools;34.0.0"`). Android Studio is not needed;
the Gradle 8.2 wrapper is included.

```bash
git clone https://github.com/nano-rex/min-recorder.git
cd min-recorder
export ANDROID_HOME=$HOME/Android/Sdk      # path to your Android SDK
./gradlew :app:assembleDebug
adb install -r app/build/outputs/apk/debug/app-debug.apk
```

## Output
Recordings are saved as WAV under `<workspace>/RecorderAndroid/recordings/`, where the
workspace is the app's Documents folder, its Downloads folder, or internal storage
(chosen in **Settings → Set Workspace Folder**; recording is disabled until one is set).

## Example

1. Open **Recorder Android** and allow microphone access.
2. **Settings → Set Workspace Folder** (required once), and optionally **Recording Source**
   to force `MIC` instead of `VOICE_RECOGNITION`.
3. Tap **Start recording**, speak, then **Stop recording**.
4. **Latest file** shows the new 16 kHz mono WAV; tap **Play** to listen. The file is
   ready to feed straight into a transcriber such as
   `omniAI/web/run.sh recording.wav`.
