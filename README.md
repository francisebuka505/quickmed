# QuickMed: build the Android APK

## Option A: no installs (GitHub builds it for you)
1. Create a free GitHub account and a new repository.
2. Upload everything in this folder (including the hidden .github folder).
3. Open the Actions tab, pick "Build QuickMed APK", press Run workflow.
4. When it finishes (about 5 minutes), open the run and download "quickmed-apk".
5. Unzip it, send app-debug.apk to your phone, tap it, and allow "Install unknown apps" when asked.

## Option B: on your computer (needs Node 18+, Java 17, Android Studio or Android SDK)
    npm install
    npx cap add android
    npx cap sync android
    # add to android/app/src/main/AndroidManifest.xml, above <application>:
    #   <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    #   <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    cd android && ./gradlew assembleDebug
APK: android/app/build/outputs/apk/debug/app-debug.apk

## Test checklist
- Speed dial and contact numbers open the phone dialer
- Alert and Text my location open the messages app with the text filled in
- Nearby asks for location permission
- Contacts and stations are still there after closing the app
The www/index.html file is the whole app. Edit it, run `npx cap sync android`, and rebuild.
