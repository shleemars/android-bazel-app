load("@rules_cc//cc:defs.bzl", "cc_library")
load("@rules_android//android:rules.bzl", "android_binary", "android_library")

cc_library(
    name = "native-lib",
    srcs = glob(["cpp/**/*.cpp"]),
    linkopts = [
        "-landroid",
        "-ldl",
        "-llog",
        "-lm",
        "-lz",
    ],
    alwayslink = 1,
)

android_library(
    name = "app_activity",
    srcs = glob(["java/**/*.java"]),
    custom_package = "com.shleemars.androidbazelexample",
    manifest = "LibraryManifest.xml",
    resource_files = glob(["res/**"]),
    deps = [
        ":native-lib",
        "@maven//:androidx_appcompat_appcompat",
        "@maven//:androidx_constraintlayout_constraintlayout",
        "@maven//:com_google_android_material_material",
    ],
)

android_binary(
    name = "app",
    custom_package = "com.shleemars.androidbazelexample",
    incremental_dexing = False,
    manifest = "AndroidManifest.xml",
    manifest_values = {
        "minSdkVersion": "21",
        "versionCode": "1",
        "versionName": "1.0.0",
        "targetSdkVersion": "29",
    },
    multidex = "native",
    deps = [":app_activity"],
)
