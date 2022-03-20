# PREREQUISITES

- [Termux](https://github.com/termux/termux-app/releases)
- Knowledge of android, java, kotlin, git, and vim 
- Android SDK (you can get it on [sdkmanager](https://developer.android.com/studio/#downloads) download the linux ver)
- Android build-tools;30.0.2 (you cant get it with sdkmanager from cmdline-tools because google) [download](https://dl-ssl.google.com/android/repository/build-tools_r30.0.2-linux.zip)
- Java SDK (pkg search openjdk and install the 17 ver)
- Git (pkg install git)
- Patience
- 2GB RAM (minimum) 3GB (recommended)
- 3GB storage (needed for gradle, android sdk & build tools and jdk)
- [JADX](https://github.com/Juby210/jadx) fork for aliucord (for decompiling discord and finding methods)
- Gradle (you get it from the plugins template)
- Building: go to root directory of your plugins folder and write 
```
sh gradlew pluginname:make
```
it will download gradle and compile, it will throw an error but still build

[REST OF PLUGIN DOCUMENTATION](/plugin-dev)
