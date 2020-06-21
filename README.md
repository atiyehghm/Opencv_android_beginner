# Opencv_android
In this project we're going to work with opencv in android. we'll start by installation then some simple projects and importing some sample projects from opencv documentation.

## what is opencv? and for what kind of applications is used?
OpenCV is an open source software library for computer vision, machine learning and image proccessing.it can aprox. do all the functionaities of image processing like identifying faces, objects and handwritings in images, producing high resolution images and so on.you can read more in this [link](https://opencv.org/about/) and [this](https://en.wikipedia.org/wiki/OpenCV)

## installation
1. Go to [the opencv site](https://opencv.org). go to releases and find the latest version of opencv and click on android.(it's recommended to download the version that is the latest version according to the version of your android studio.For example my android studio version is 3.5.3 so i downloaded 3.4.10)

![alt step1](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/1_installation.png)

2. Once the download finished unzip it in some location.(for those who are on windows, `c:\program files` is recommended. and for those on mac and linux, `Users/yourname/android/opencv-android-sdk` is recommended.

3. Start a new project in android studio. then from the menu bar select `new -> import module`.

![alt step3](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/2_installation.png)

4. Select the java file in opencv-sdk and click next and then finish.

![alt step4](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/3_installation.png)

5. After adding the java file you will get the following error.click on `remove minSdkVersion and sync project` and then click on `Do refactor` to fix this error. This error basically happens because the minSdkversion of the opencv librery is different from the version in your app's androidManifest.

![alt step5](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/4_installation.png)

6. Go to the `file -> project structure -> dependencies -> All modules -> + ->module dependency -> app` and then mark `opencv3410`.

![alt step6](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/6_installation.png)

7.From `gradle scripts`, open `build.gradle(app)`. make sure the version of `compileSdkVersion` and `targetSdkVersion` are same.(in my case they are both 29)

![alt step7](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/7_installation.png)

8.From `gradle scripts`, open `build.gradle(opencvlibrary)`.change the version of `compileSdkVersion` and `targetSdkVersion` to the number that you checked in perivious step.(in my case, 29).then click on `sync now`.

![alt step8](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/8_installation.png)

9.The next step is adding JNI libraries to our app.this is basically because we want to use native c++ APIs of opencv in our app.Right click on app then `new -> folder -> JNI folder`. then mark `change folder location` and write `src/main/jniLibs` for the location.

![alt step9-1](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/9_installation.png)

![alt step9-2](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/10_installation.png)

10.Copy the contents of `native` folder in `opencv- sdk` and paste then in `jniLibs`.

![alt step10](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/11_installation.png)

11. Now integrating opencv library in android project is done.write this code below in `MainActivity` method to make sure you've added opencv correctly.

```
private static String TAG = "Main Activity";
static {
        if (OpenCVLoader.initDebug()){
            Log.i(TAG, "******************************Opencv is added successfullu!");
        }
        else
            Log.i(TAG, "^^^^^^^^^^^^^^^^^^^^^^^^^^^^Opencv is not working properly!!");
    }
 ```

## OpenCV packages
After creating an opencv android project, let's take a look at packages within opencvLibrary

![alt packages](https://github.com/atiyehghm/Opencv_android/blob/master/README.md_images/packages.png)

| package name  | description   |
| ------------- |:-------------:|
| Android       | The main purpose of this package is to make opencv usable on android devices.               |
| calib3d       | If you are capturing an object, this package can determine the 3D coordinates of the object.|
| core          | It provides the base functionality of opencv. For example, it does the mathematical or matrix operations or some implemented algorithms.(Note that it does not do any image processing.)|
|features2d     | It's a package for 2D image feature detectors and decriptor extrcators.                     |  
|dnn            | This is a package for deep neural network algorithms.                                       |
|imgcodecs      | This package loads images from disc or writes on disc. This is used in those applications that don't get the image from camera. It's used for reading single or multiple images of different formats.|
|imgproc        | It has all the functions for manipulating images. you can use it to apply effects, blur image, write text on image and so on.|
|ml             | This package is for machine learning(artificial intelligence). It has some training algorithms for computer vision.|
|osgi           | This package provides an easy way to load opencv's native libraries from java bundle.       |
|photo          | It's used for image enhancement. You can apply manipulations like setting the contrast, hue, saturation, etc.|
|utils          | It's used for converting image data from one mathematical format to another.                |
|video          | It does video processing like applying filters, tracking objects and more.                  |
|videoio        | It is used for reading and writing video files of any format.                               |


