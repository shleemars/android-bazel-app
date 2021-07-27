# Android Bazel App

Template for Android App with Bazel build system.

## Instructions
- Install Android SDK Build-Tools 29, Android NDK
- Edit WORKSPACE file, add android_sdk_repository path and android_ndk_repository path
- Install Bazel 4.1.0 or Bazelisk 

## Build
```shell
$ bazel build --fat_apk_cpu=arm64-v8a //app/src/main:app
$ adb install bazel-bin/app/src/main/app.apk
```

## Using mobile-install
```shell
$ bazel mobile-install --start_app --fat_apk_cpu=arm64-v8a //app/src/main:app
```

If you are a MacOS user, you need to install the `futures` package. 
```shell
$ curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
$ python get-pip.py
$ python -m pip install futures
```
