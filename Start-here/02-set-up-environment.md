# Set up your environment

## Introduction
You need four things: Android Studio, a way to run apps (emulator or real phone), Git, and a GitHub account.

## Learning outcomes
- Install Android Studio and create a project.
- Run an app on an emulator or a physical device.
- Push a project to GitHub.

## Lesson

### 1. Machine check
Android Studio is heavy. Aim for 8 GB RAM minimum (16 GB is comfortable), an SSD, and about 20 GB free disk. On a low-RAM laptop: close the browser while building, and prefer a **physical phone** over the emulator (it uses far less memory).

### 2. Install Android Studio
Download the latest stable version from [developer.android.com/studio](https://developer.android.com/studio). The installer includes the Android SDK, the emulator and a bundled JDK. Kotlin support is built in, so you don't install Kotlin separately.

### 3. Create your first project
1. New Project → **Empty Activity** (this uses Jetpack Compose).
2. Name: `HelloAndroid`. Package: `com.example.helloandroid`. Language: Kotlin.
3. Minimum SDK: pick what Studio recommends.
4. Wait for **Gradle sync** to finish (first time can be slow, and it needs internet).

### 4. Run it
- **Emulator:** Device Manager → Create Device → pick a Pixel → download a system image → Run.
- **Real phone:** Settings → About phone → tap *Build number* 7 times → Developer options → enable **USB debugging** → plug in → accept the prompt → select your phone → Run.

### 5. Git and GitHub
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
cd path/to/project
git init
git add .
git commit -m "chore: first project"
git branch -M main
git remote add origin https://github.com/YOUR-USER/my-android-path.git
git push -u origin main
```
Android Studio's `.gitignore` is good. This repo includes one too, so you never commit `local.properties` or keystores.

### 6. Know the Studio panels
Project (files) · Editor · Logcat (app logs) · Build output · Device Manager · Preview (Split/Design buttons on a Compose file).

## Practice
1. Create and run `HelloAndroid`.
2. Change the greeting text in `MainActivity.kt`, run again, and see it update.
3. Push the project to GitHub.

## Knowledge check
- Why don't you install Kotlin separately?
- What is Gradle sync and when does it run?
- How do you enable USB debugging?

## Additional resources
- [Install Android Studio](https://developer.android.com/studio/install)
- [Run apps on a hardware device](https://developer.android.com/studio/run/device)
- [Android Emulator](https://developer.android.com/studio/run/emulator)

Previous: [How this path works](01-how-this-works.md) · Next: [Variables, types and functions](../01-kotlin-foundations/01-variables-types-functions.md)
