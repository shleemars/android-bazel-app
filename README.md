# Android Bazel App

Template for Android App with Bazel build system.

## Instructions
- (MacOS) Install developer's tools
```shell
xcode-select --install
```
- (MacOS) Install HomeBrew and Python
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
```shell
brew install python
```

- Install JRE or JDK
  - Install `default-jdk` on Ubuntu 20.04  
- Install Android SDK Build-Tools 29, Android NDK
- Edit WORKSPACE file, modify `path` variables on android_sdk_repository, android_ndk_repository
- Install `Bazelisk` or `Bazel` 4.1.0 (I prefer `Bazelisk`)
- Install python
  - Install `python-is-python3` on Ubuntu 20.04

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
