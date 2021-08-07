# Android Bazel App
This repo provides Android App template for Bazel build system.

# Prerequisites

To build Android application with bazel, followings are needed.

- Java Runtime Environment(JRE) or Java Development Environment(JDK)
- Python(`/usr/bin/env python`) and relavant packages
- Bazelisk or Bazel 4.1.0

## Instructions for MacOS
Install **developer's tools**. You can skip if you already installed Xcode.
```shell
xcode-select --install
```

Install **Java Development Kit 11**.
- Azul OpenJDK https://www.azul.com/downloads/?package=jdk
- Oracle JDK https://www.oracle.com/kr/java/technologies/javase-jdk11-downloads.html

Install **pip**. You can skip if you already installed pip.
```shell
curl -fsSL https://bootstrap.pypa.io/pip/2.7/get-pip.py | python -
```

Install Python **`futures`** packages.
```shell
python -m pip install futures
```

Install **HomeBrew**.
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install **Bazelisk**.
```shell
brew install bazelisk
```

## Instructions for Ubuntu 20.04
Install **Java Development Kit 11**, **Go**, **Python**.
```shell
sudo apt-get install default-jdk golang python-is-python3
```

Install **Bazelisk**.
```shell
go get github.com/bazelbuild/bazelisk
```

Add **`$HOME/go/bin`** to environment variable `PATH`. My recommendation is appending the following line to your profile file like `$HOME/.profile`.
```shell
export PATH=$PATH:$HOME/go/bin
```

## Instructions for MS-Windows
TODO

# Android SDK 

With Android Studio, you can install the Android SDK as follows:
1. Click **Tools > SDK Manager**
2. In the **SDK Platforms** tab, select **Android 10.0(Q)**
3. In the **SDK Tools** tab, select **Android SDK Build-Tools 29.0.3**, **NDK (Side by side) 21.4.7075529**, **Android SDK Command-line Tools(latest)**
4. Click **OK** to install the SDK

Export `ANDROID_SDK`, `ANDROID_NDK_HOME` environment variables. The paths are depends on your configurations, following are just typical path.

**MacOS**
```shell
export ANDROID_HOME=$HOME/Library/Android/sdk
export ANDROID_NDK_HOME=$HOME/Library/Android/sdk/ndk/21.4.7075529
```

**Ubuntu**
```shell
export ANDROID_HOME=$HOME/Android/Sdk
export ANDROID_NDK_HOME=$HOME/Android/Sdk/ndk/21.4.7075529
```

**MS-Windows**
TODO

# Build
Clone the project.

```shell
git clone https://github.com/shleemars/android-bazel-app.git
```
```shell
cd android-bazel-app
```

Build project.

```shell
bazel build --fat_apk_cpu=arm64-v8a //app/src/main:app
```

## Build with `mobile-install`
You can build, install and run the app with single command `mobile-install`.

```shell
bazel mobile-install --start_app --fat_apk_cpu=arm64-v8a //app/src/main:app
```
