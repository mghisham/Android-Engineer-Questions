# Android-Engineer-Questions

## Basics

<details>
<summary>1. What is Application</summary>

> The Application class in Android is the base class within an Android app that contains all other components such as activities and services. The Application class, or any subclass of the Application class, is instantiated before any other class when the process for your application/package is created.
</details>
<details>
<summary>2. What is Context</summary>

> A Context is a handle to the system; it provides services like resolving resources, obtaining access to databases and preferences, and so on. An Android app has activities.Context is like a handle to the environment your application is currently running in.
> Application Context: This context is tied to the lifecycle of an application. The application context can be used where you need a context whose lifecycle is separate from the current context or when you are passing a context beyond the scope of an activity.
> Activity Context: This context is available in an activity. This context is tied to the lifecycle of an activity. The activity context should be used when you are passing the context in the scope of an activity or you need the context whose lifecycle is attached to the current context.
</details>
<details>
<summary>3. Why bytecode cannot be run in Android</summary>

> Android uses DVM (Dalvik Virtual Machine ) rather using JVM(Java Virtual Machine).
</details>
<details>
<summary>4. What is a BuildType in Gradle? And what can you use it for</summary>

> Build types define properties that Gradle uses when building and packaging your Android app.
A build type defines how a module is built, for example whether ProGuard is run.
> A product flavour defines what is built, such as which resources are included in the build.
Gradle creates a build variant for every possible combination of your project's product flavours and build types.
</details>
<details>
<summary>5. Explain the build process in Android</summary>

> First step involves compiling the resources folder (/res) using the aapt (android asset packaging tool) tool. These are compiled to a single class file called R.java. This is a class that just contains constants.
Second step involves the java source code being compiled to .class files by javac, and then the class files are converted to Dalvik bytecode by the "dx” tool, which is included in the sdk 'tools'. The output is classes.dex.
The final step involves the android apkbuilder which takes all the input and builds the apk (android packaging key) file.
</details>
<details>
<summary>6. What is the Android Application Architecture</summary>

> Android application architecture has the following components: 
Services − It will perform background functionalities
Intent − It will perform the inter connection between activities and the data passing mechanism
Resource Externalization − strings and graphics
Notification − light, sound, icon, notification, dialog box and toast
Content Providers − It will share the data between applications
</details>
<details>
<summary>7. Describe activities</summary>

> Activities are basically containers or windows to the user interface.
</details>
<details>
<summary>8. Launch modes in Android</summary>

#### Standard: 
It creates a new instance of an activity in the task from which it was started. Multiple instances of the activity can be created and multiple instances can be added to the same or different tasks.
Eg: Suppose there is an activity stack of A -> B -> C. 
Now if we launch B again with the launch mode as "Standard", the new stack will be A -> B -> C -> B.
#### SingleTop: 
It is the same as the standard, except if there is a previous instance of the activity that exists in the top of the stack, then it will not create a new instance but rather send the intent to the existing instance of the activity.
Eg: Suppose there is an activity stack of A -> B.
    Now if we launch C with the launch mode as "singleTop”, the new stack will be A -> B -> C as usual.
    Now if there is an activity stack of A -> B -> C.
    If we launch C again with the launch mode as "singleTop”, the new stack will still be A -> B -> C.
#### SingleTask: 
A new task will always be created and a new instance will be pushed to the task as the root one. So if the activity is already in the task, the intent will be redirected to onNewIntent() else a new instance will be created. At a time only one instance of activity will exist.
Eg: Suppose there is an activity stack of A -> B -> C -> D.
    Now if we launch D with the launch mode as "singleTask”, the new stack will be A -> B -> C -> D as usual.
    Now if there is an activity stack of A -> B -> C -> D. 
    If we launch activity B again with the launch mode as "singleTask”, the new activity stack will be A -> B. Activities C and D will be destroyed.
#### SingleInstance: 
Same as single task but the system does not launch any activities in the same task as this activity. If new activities are launched, they are done so in a separate task.
Eg: Suppose there is an activity stack of A -> B -> C -> D. If we launch activity B again with the launch mode as "singleInstance”, the new activity stack will be:
```
    Task1 : A -> B -> C
    Task2 : D
```
</details>
<details>
<summary>9. Mention two ways to clear the back stack of Activities when a new Activity is called using intent</summary>

> The first approach is to use a FLAG_ACTIVITY_CLEAR_TOP flag. The second way is by using FLAG_ACTIVITY_CLEAR_TASK and FLAG_ACTIVITY_NEW_TASK in conjunction.
</details>
<details>
<summary>10. Describe content providers</summary>

> A ContentProvider provides data from one application to another, when requested. It manages access to a structured set of data. It provides mechanisms for defining data security. ContentProvider is the standard interface that connects data in one process with code running in another process.
When you want to access data in a ContentProvider, you must instead use the ContentResolver object in your application's Context to communicate with the provider as a client. The provider object receives data requests from clients, performs the requested action, and returns the results.
</details>
<details>
<summary>11. Describe services</summary>

A Service is an application component that can perform long-running operations in the background, and it doesn't provide a user interface. It can run in the background, even when the user is not interacting with your application. These are the three different types of services:
### Foreground Service: 
A foreground service performs some operation that is noticeable to the user. For example, we can use a foreground service to play an audio track. A Notification must be displayed to the user.
### Background Service: 
A background service performs an operation that isn't directly noticed by the user. In Android API level 26 and above, there are restrictions to using background services and it is recommended to use WorkManager in these cases.
### Bound Service: 
A service is bound when an application component binds to it by calling bindService(). A bound service offers a client-server interface that allows components to interact with the service, send requests, receive results. A bound service runs only as long as another application component is bound to it.
</details>
