Android overview
=================
* linux-based platform which runs on mobile phones and pads. 
* has a considerable market share

### Android development
* Java SDK with emulators 
    * Eclipse plugin
* Native SDK available for special cases

### Android devices
* Hundreds of devices, mostly touch screen
* [Most devices](http://developer.android.com/resources/dashboard/platform-versions.html) are at runtime 2.1 or later, latest and greatest is 4.0.3. 
* Multiple resolutions and aspect ratios, keyboard configurations.

Installation
============
**All you need to get started is available in the network share apps folder 'Android' (\\SPICA\Winapps\Android).**

1. Install Eclipse
2. Install ADT plugin from update site https://dl-ssl.google.com/android/eclipse/ and restart eclipse
3. An Android wizard should appear automatically, run through it. Otherwise install latest Android SDK runtime 4.0.3, platform tools and USB drivers via Eclipse menu Window->Android SDK Manager.
4. Open Window->Android SDK Manager and install the default selected items. You'll need the ARM EABI to run the emulator.

**Online installation is the most easy**. 

### Off-line installation
Downloading the SDK runtime(s) takes a long time, so alternatively go for
off-line installation:

1. Copy android-15_r01.zip from network share
2. Unzip to your sdk location 'platform' folder - for example "C:\Users\trs\android-sdks\platforms"
3. Copy tools_r16-windows.zip and platform-tools_r10-windows.zip
4. Unzip to root of sdk location - for example "C:\Users\trs\android-sdks\"
5. From Eclipse, launch 'Android SDK Manager' and check that Tools and Android 4.0.3 is installed.

Some troubleshooting info [here](http://qdevarena.blogspot.com/2010/05/download-android-sdk-standalone-for.html).
Task 1 - Hello world
====================

### a. Create new project and launch emulator
* Create new Android project called 'HelloWorld'
* Launch emulator via project 'run as Android application'. 
    * Create a new virtual device

### b. Change hello world text
Change text from 'Hello world' to 'Hello Antares'

Hint: Check the files in the 'res' directory

### c. Add button in XML
Add a button to GUI by modifying 'main.xml' in 'res/layout'. Add the XML

    <Button android:id="@+id/button"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Hello, I am a Button" 
    />

### d. Find XML button view at runtime
Access XML-generated button instance from within the HelloWorldActivity.onCreate(..) method.

Hint: Use the method findViewById(..) method together with auto-generated class R.id.xxx.

### e. Add button click listener
Connect a click listener to the button. Log text to console on click:

            Log.d(getClass.getSimpleName(), "Button was clicked!");

Hint: Use method Button.setOnClickListener(..).

Hint: Show view 'LogCat' in Eclipse

Task 2 - create new Activity
============================
Check out the topmost figure in [Android documentation](http://developer.android.com/reference/android/app/Activity.html).

### a. Create new Activity class
Create a new class 'MyActivity' with extends the Activity class. Copy the 'onCreate' method from HelloWorldActivity.

### b. Create a new layout file for MyActivity
Create a new layout xml file in 'res/layout'. Change the MyActivity.onCreate class so that it loads the new layout file.

### c. Start 'MyActivity'
Start the activity from the button click listener in task 1. 

Launch the new activity like this: 

    Intent i = new Intent(this, MyActivity.class);
    startActivity(i);

Hint: Add activity to AndroidManifest.xml

Task 3 - on-device debugging
============================
Enable developer mode in you Andorid phone via settings. Connect your Android phone to your PC using an USB cable. 

Run the application on the phone. 

Task 4 - multiple screen resolutions
=====================================
## a. Resource folders
[Determine](http://developer.android.com/guide/practices/screens_support.html) what the resource folders

* drawable-ldpi
* drawable-mdpi
* drawable-hdpi 

are used for. 

## b. Image view
Create directory 'res/drawable' and copy file [android.png](http://www.mediafire.com/imgbnc.php/1ba890f73cfdc925e08b13fe34d5141e6g.jpg) into the directory. Then add the following to main.xml:

    <ImageView 
      android:id="@+id/android_image"
      android:src="@drawable/android"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
    />

Use AVD Manager to create multiple virtual (emulator) devices to see how different devices see the same image. Then add scaled versions to ldpi, mdpi and hdpi and try again.