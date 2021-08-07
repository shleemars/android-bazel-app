# Android Bazel App
This repo provides Android App template for Bazel build system.

- Android SDK Build-Tools 29
- Android NDK

# Prerequisites

To build Android application with bazel, followings are needed.

- Java Runtime Environment(JRE) or Java Development Environment(JDK)
- Python(`/usr/bin/env python`) and relavant packages
- Bazelisk or Bazel 4.1.0

## Instructions for MacOS prerequisites
- Install developer's tools (including toolchains)
```shell
xcode-select --install
```

- Install HomeBrew for OpenJDK 11
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

- Install OpenJDK 11 and bazelisk
```shell
brew install opendjk@11 bazelisk
```

- Install pip (You can skip if you already installed pip) 
```shell
curl -fsSL https://bootstrap.pypa.io/pip/2.7/get-pip.py | python -
```

- Install python `futures` packages
```shell
python -m pip install futures
```

## Instructions for Ubuntu 20.04
- Install OpenJDK 11, golang, python
```shell
sudo apt-get install default-jdk golang python-is-python3
```

## Instructions for MS-Windows
Not ready yet

# Android SDK 
- Install Android SDK Build-Tools 29, Android NDK
- Edit WORKSPACE file, modify `path` variables on android_sdk_repository, android_ndk_repository

## Build
If you want to build only
```shell
bazel build --fat_apk_cpu=arm64-v8a //app/src/main:app
```

You can install the app using `adb`
```shell
adb install bazel-bin/app/src/main/app.apk
```

## Build & Install & Run `mobile-install`
You can build & install & run the app with single command `mobile-install`

```shell
bazel mobile-install --start_app --fat_apk_cpu=arm64-v8a //app/src/main:app
```

## Issues
### missing package `futures` on MacOS
If you get a error that the `futures` package is missing, you need to install the `futures` package. But MacOS doesn't have `pip` for python2.7, you need to install `pip` for python2.7 at first.

Install pip for python2 
```shell
curl -fsSL https://bootstrap.pypa.io/pip/2.7/get-pip.py | python -
```

Install `futures` package 
```shell
python -m pip install futures
```
