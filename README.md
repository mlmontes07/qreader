#QREader    [![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.github.nisrulz/qreader/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.github.nisrulz/qreader) [![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-QREader-green.svg?style=true)](https://android-arsenal.com/details/1/3478)

A library that uses google's mobile vision api and simplify the QR code reading process 

#Integration
- QREader is available in the MavenCentral, so getting it as simple as adding it as a dependency
```gradle
compile 'com.github.nisrulz:qreader:1.0.1'
```

#Usage
+ First add a `SurfaceView` to your layout and give it an id
```java
<SurfaceView
        android:id="@+id/camera_view"
        android:layout_width="320dp"
        android:layout_height="320dp"/>
```

+ Then in your Activity code reference the `SurfaceView`
```java
SurfaceView surfaceView = (SurfaceView) findViewById(R.id.camera_view);
```

+ Next setup the config
    + The default config uses autofocus, back camera and preview size set at 800x800 and is referenced as below
    ```java
    QREader.getInstance().setUpConfig();
    ```
    
    + There are other config methods to give you more granular configurations
    ```java
    // Disable/Enable autofocus
    // Choose between Front facing or Back facing camera | Possible arguments : CameraSource.CAMERA_FACING_BACK /  CameraSource.CAMERA_FACING_FRONT
    QREader.getInstance().setUpConfig(boolean autofocus_enabled, int facing);
    // Change all the config values
    QREader.getInstance().setUpConfig(boolean autofocus_enabled, int width, int height, int facing);
    ```   


+ Lastly call `QREader.getInstance().start()` with required arguments in your Activity code, to start reading 
QR code.
```java
QREader.getInstance().start(this, surfaceView, new QRDataListener() {
        @Override
        public void onDetected(final String data) {
            Log.d("QREader", "Value : " + data);
        }
    });
```

*where*

|argument|type|
|---|---|
|this|`Context`|
|surfaceView|`SurfaceView`|
|new QRDataListener()|`QRDataListener`|

License
=======

    Copyright 2016 Nishant Srivastava

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.