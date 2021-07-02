# Crash Reports

Firebase Crashlytics is a lightweight, real-time crash reporter that helps you track, prioritize, and fix stability issues that erode your app quality. Crashlytics saves you troubleshooting time by intelligently grouping crashes and highlighting the circumstances that lead up to them.

A few steps must be done in our project, in order to sync it up with Firebase Crashlytics:

### Setup your Firebase Project

Due to firebase/crashlytics relies on google services (com.google.gms.google-services), you need to download google-services.json which should be created from the firebase console.

### Add the Firebase Crashlytics plugin to your app

In your project-level build.gradle file, add the Crashlytics Gradle plugin as a buildscript dependency.

```
classpath 'com.google.gms:google-services:4.3.5'
classpath 'com.google.firebase:firebase-crashlytics-gradle:2.5.2'
```

In your app-level build.gradle file, apply the Crashlytics Gradle plugin:
 
```
apply plugin: 'com.google.gms.google-services'
apply plugin: 'com.google.firebase.crashlytics'
``` 

Declare the dependency for the Crashlytics Android library in your module (app-level) Gradle file (usually app/build.gradle).

```
implementation platform('com.google.firebase:firebase-bom:27.0.0')
implementation 'com.google.firebase:firebase-analytics'
implementation 'com.google.firebase:firebase-crashlytics-ndk'
implementation "com.google.firebase:firebase-messaging"
```

Add the following configuration for your release build:

```
firebaseCrashlytics {
    // Enable processing and uploading of native symbols to Crashlytics servers.
    // By default, this is disabled to improve build speeds.
    // This flag must be enabled to see properly-symbolicated native
    // stack traces in the Crashlytics dashboard.
    nativeSymbolUploadEnabled true
    unstrippedNativeLibsDir "obj"
}
```

**nativeSymbolUploadEnabled**: This flag, when enabled, will create a new Gradle task, that will be called uploadCrashlyticsSymbolFileBUILD_VERSION. In order to access these tasks go to the Gradle tab on the right side of the project. 

**unstrippedNativeLibsDir**: The value for this variable, will be the debug symbols that will be uploaded to Crashlytics and the ones we will refer to. You should receive those obj files separately from the SDK package. Once downloaded, place them under the root of the project with the folder name `obj` to match with the above configuration. 

Once the Gradle is synched, you should run manually at first the `generateCrashlyticsSymbolFile{BUILDVARIANT}` which will create a .cSYM file for each of our arch/libfile.so. When this task is completed, `/build/crashlytics/build/version/nativeSymbols` contains the .cSYM files for the architectures.

After the previous step has been confirmed, you should run `uploadCrashlyticsSymbolFile{BUILDVARIANT}` task which will package each of the previous .cSYM files and upload them to the crashlytics backend.

### Testing the integration

Compile the apk and install it, force a crash or an exception, and observe that those reports are recorded under your crashlytics tab in your firebase project.

You can get more information about crash reporting from the official firebase documentation:
https://firebase.google.com/docs/crashlytics/ndk-reports