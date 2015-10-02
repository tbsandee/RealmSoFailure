# RealmSoFailure
Demonstrates failure to properly include .so included in AAR files with Android Gradle Plugin 1.4.0-beta[1-4].

Change the plugin version to 1.3.1 and all works fine.

The dependency added is this:
```compile 'io.realm:realm-android:0.82.2'```

and the code to trigger the failure is in `MainActivity.java`:
```Realm.getInstance(this);```

Here's the error:

```
 FATAL EXCEPTION: main
                         E  Process: com.example.ben.testrealmapp, PID: 7973
                         E  java.lang.UnsatisfiedLinkError: Couldn't load realm-jni from loader dalvik.system.PathClassLoader[dexPath=/data/app/com.example.ben.testre
                            almapp-1.apk,libraryPath=/data/app-lib/com.example.ben.testrealmapp-1]: findLibrary returned null
                         E      at java.lang.Runtime.loadLibrary(Runtime.java:358)
                         E      at java.lang.System.loadLibrary(System.java:526)
                         E      at io.realm.internal.RealmCore.loadLibrary(RealmCore.java:117)
                         E      at io.realm.internal.SharedGroup.<clinit>(SharedGroup.java:35)
                         E      at io.realm.Realm.<init>(Realm.java:207)
                         E      at io.realm.Realm.createAndValidate(Realm.java:597)
                         E      at io.realm.Realm.create(Realm.java:567)
                         E      at io.realm.Realm.getInstance(Realm.java:413)
                         E      at io.realm.Realm.getInstance(Realm.java:370)
                         E      at io.realm.Realm.getInstance(Realm.java:351)
                         E      at com.example.ben.testrealmapp.MainActivity.onCreate(MainActivity.java:33)
                         E      at android.app.Activity.performCreate(Activity.java:5451)
                         E      at android.app.Instrumentation.callActivityOnCreate(Instrumentation.java:1093)
                         E      at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2298)
                         E      at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:2392)
                         E      at android.app.ActivityThread.access$900(ActivityThread.java:169)
                         E      at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1280)
                         E      at android.os.Handler.dispatchMessage(Handler.java:102)
                         E      at android.os.Looper.loop(Looper.java:146)
                         E      at android.app.ActivityThread.main(ActivityThread.java:5487)
                         E      at java.lang.reflect.Method.invokeNative(Native Method)
                         E      at java.lang.reflect.Method.invoke(Method.java:515)
                         E      at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:1283)
                         E      at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:1099)
                         E      at dalvik.system.NativeStart.main(Native Method)
```
