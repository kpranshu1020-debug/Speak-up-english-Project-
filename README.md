# SpeakUp English — Flutter Android starter

A starter app for Indian students in Classes 9–11. Includes an offline lesson set, Hindi explanations, Android speech recognition integration, text-to-speech, local progress, and a sample rule-based tutor.

## Important limitations
- This is the source project, not a precompiled APK.
- Speech recognition availability depends on the Android device/service and may require internet.
- The AI Tutor currently uses sample offline replies. For real open-ended AI responses, connect a secure backend/API. Do not place secret API keys inside the mobile app.
- The feedback is basic recognised-word overlap, not professional pronunciation/accent scoring.
- Before distributing to minors, add a privacy notice, parental consent where applicable, and data minimisation.

## Build APK with GitHub Actions (phone-friendly route)
1. Sign in to GitHub and create a new **public or private repository** named `speakup-english`.
2. Upload the contents of this ZIP into the repository's root (the `lib` folder, `pubspec.yaml`, and `.github` folder must be at root). On GitHub mobile web, use **Add file → Upload files** if available.
3. Open **Actions**. If prompted, enable workflows.
4. Select **Build Android APK** and tap **Run workflow**. Or push a commit to `main`.
5. When it finishes successfully, open the run, scroll to **Artifacts**, and download `speakup-english-apk`.
6. Extract the artifact ZIP to get `app-release.apk`, then install it on your Android phone. You may need to allow installs from your browser/files app.

## Local build
Install Flutter SDK, then run:
```bash
flutter pub get
flutter build apk --release
```

## Permissions
The Android app needs microphone permission for speech input. Depending on the plugin version, verify the Android manifest permission and test on a real device. Add the following inside `android/app/src/main/AndroidManifest.xml` if absent:
```xml
<uses-permission android:name="android.permission.RECORD_AUDIO"/>
```
Flutter creates the `android/` platform folder when you run `flutter create .` in a project directory. If uploading this starter to GitHub, generate platform files first in a Flutter environment with `flutter create .`, commit the generated `android/` directory, then run the workflow above. A pure source folder without the generated `android/` directory will not build in GitHub Actions.
