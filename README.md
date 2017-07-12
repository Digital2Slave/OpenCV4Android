# OpenCV4Android
Repo about create your own opencv-android lib without install opencv manager apk.

## Steps

- download [opencv-2.4.13.2-android-sdk.zip](https://sourceforge.net/projects/opencvlibrary/files/opencv-android/2.4.13/opencv-2.4.13.2-android-sdk.zip/download)
- create an android project and named **OpenCV4Android**
- create an android library and named **opencv**, edit Package name: **org.opencv**
- unzip **opencv-2.4.13.2-android-sdk.zip**, and copy all subfolders in **OpenCV-android-sdk/sdk/java/src/org/opencv** to android opencv library **opencv/src/main/java/org/opencv**
- do the following operate in android opencv library **opencv/src/main/java/org/opencv/android**:
    - delete **AsyncServiceHelper.java**
    - comment some code in **OpenCVLoader.java**
    ```
    //    public static boolean initAsync(String Version, Context AppContext,
    //            LoaderCallbackInterface Callback)
    //    {
    //        if (initDebug()) {
    //            Callback.onManagerConnected(LoaderCallbackInterface.SUCCESS);
    //            return true;
    //        }
    //        Log.w(TAG, "OpenCV binaries are not packaged with application. Trying to use OpenCV Manager...");
    //        return AsyncServiceHelper.initOpenCV(Version, AppContext, Callback);
    //    }
    ```
- copy **OpenCV-android-sdk/sdk/java/res/values/attrs.xml** to android opencv library **opencv/src/main/java/res/values/**
- modify android opencv library file **opencv-android/src/main/java/res/values/string.xml**
  ```
  <resources>
  <string name="app_name">OpenCV-2.4.13.2</string>
  </resources>
  ```
- create **jniLibs** folder in android opencv library **opencv/src/main**
- copy what you need subfolder in **OpenCV-android-sdk/sdk/native/libs** to android opencv library **opencv/src/main/jniLibs**
- Import opencv library to app by the following:
    1. click **File->Project Structure...**
    2. click **app** under **Modules** category, and then click **Dependencies** on the right
    3. click `+` around **Dependencies** and choose **3 Module Dependency**
    4. choose **:opencv**, and click **OK**, **OK**

## Find the aar files

After you run the app, you should find the android opencv library aar files in **opencv/build/outputs/aar**, which like
```
opencv-debug.aar
opencv-release.aar
```

## How to import the aar file

reference [this](http://stackoverflow.com/questions/16682847/how-to-manually-include-external-aar-package-using-new-gradle-android-build-syst)

## Reference

[opencv-android](https://github.com/steveliles/opencv-android)
