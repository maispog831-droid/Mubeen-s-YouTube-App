# YouTubeWebViewApp — Android 4.4.4 / API 19

Lightweight Java-only WebView kiosk intended for an Android 4.4.4 car tablet.

## Build

- Android Studio with a compatible JDK (AGP 7.4.2 requires JDK 11–17; JDK 17 is recommended).
- Install Android SDK Platform 30.
- Open this folder as an Android Studio project and Sync/Build.
- Run `assembleDebug` to create an automatically signed test APK.

The project intentionally has **no AndroidX/AppCompat/third-party dependencies**.
`minSdkVersion` and `targetSdkVersion` are both 19.

## APK location

`app/build/outputs/apk/debug/app-debug.apk`

## Behaviour

- Opens `https://www.youtube.com/` on first launch.
- Uses a KitKat-compatible Chrome 30-style mobile user agent.
- If the full YouTube endpoint produces a network/page error, it makes one fallback attempt at `https://m.youtube.com/`.
- HTTP/HTTPS links stay inside the WebView; non-web schemes are not launched.
- Back, forward and reload controls are provided.
- HTML5 fullscreen is handled when supported by the KitKat WebView.
- TLS certificate errors are rejected rather than bypassed.

## Important limitation

The APK being compatible with Android 4.4.4 does **not** make the modern YouTube website compatible with the old Chromium WebView. The tablet's WebView engine may still fail to render current YouTube pages or play modern streams. If that happens, the app wrapper itself is working; the limiting factor is the old WebView/YouTube compatibility.
