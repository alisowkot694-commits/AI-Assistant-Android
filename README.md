# AI Assistant — Android APK project

This project packages the hosted AI Assistant web app in an Android WebView and provides a native Android app-launch bridge plus a foreground wake-phrase service.

## Important behavior and limitations

- The hosted AI interface is loaded from the URL configured in `MainActivity.kt`. The actual web-app source is not included in this ZIP, so its availability and its Bengali/English conversational features depend on that hosted website.
- The wake phrase service listens for “AI Assistant” (including common Bengali-script renderings) using Android's speech-recognition service. It requires microphone permission and displays an ongoing foreground notification while active.
- Android 12–15 and phone manufacturers may restrict background microphone use or stop services to save battery. The user must grant microphone permission, and may need to allow background activity / unrestricted battery use in phone settings. No Android app can guarantee uninterrupted always-on listening on every device.
- Speech recognition may use Google's/another installed speech-recognition provider and may require internet. Recognition language behavior varies by device.
- The notification includes a **Stop listening** action.

## Build APK automatically with GitHub Actions

1. Upload the contents of this ZIP into the root of a GitHub repository (not the ZIP file itself).
2. Open the repository's **Actions** tab.
3. Select **Build AI Assistant APK** and press **Run workflow** (or push to `main`/`master`).
4. When the workflow succeeds, open that run and download the `AI-Assistant-debug-apk` artifact.
5. Extract the downloaded artifact ZIP to get `app-debug.apk`, then install it on your Android phone.

The workflow uses JDK 17 and Gradle 8.7. This project does not require a locally installed Android Studio to use the GitHub build workflow.
