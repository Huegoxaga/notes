# Android Development with Java

## Introduction

- Android is a mobile operation system based on a modified version of the Linux Kernel
- Linux OS defines the basic file system, I/O, and low level hardware interface for mobile devices and Android provides the user interface or service level access
- Android Studio is the IDE for Android App Development
- Android SDK is provided by various versions of SKD platforms. Each marjor platform version has a name. E.g. `Android 10.9` is called `Q`.
- Each SDK platform version is associated with an API level, API level is used to determined the apps compatibility
  - Forward compatibility or upward compatibility is guaranteed (lower level app works on all newer API level platform

## Setup

### Installation

- [Download](https://www.oracle.com/ca-en/java/technologies/javase-downloads.html) and install the lastest Java SE Development Kit.
  - For Mac using Brew, run `brew install java --cask ` and run `brew info java --cask` to verify.
- [Download](https://developer.android.com/studio) and install Android Studio.
  - For Mac, run `brew install android-studio --cask`.
- Install the preferred SDK platform for the devices to use when testing in SDK Manager
- On machines running macOS Big Sur, Android Studio 4.1 might freeze when you open a dialog, run `defaults write com.google.android.studio AppleWindowTabbingMode manual` to fix this issue

### Open a Project

- Create a new project
  - Select `start a new project`.
  - Select the `Empty Activity` template(recommanded)
  - The package name is the unique identifier of the app. Usually it is the organization or personal domain name in reverse order.
- Open an existing project
  - In the welcome page, select and open the existing project folder
  - Open the existing project's gradle file with Andriod Studio.
  - Open the from the menu bar.

### Configuration

- In the preference menu, one can:
  - Change color and font size
  - Enable auto import
  - And prefix for Java name convention
  - Setup version control

### Run Apps

#### Emulator

- Install the required images in the SDK manager
  - If the host machine has an Intel CPU, install the `Intel X86` images.
    - Install the `Intel X86 Emulator Accelerator` in the SDK Tools page for a faster performance
    - `Google APIs Intel X86` includes Google APIs in the image
  - If the host machine has an ARM CPU, install the `ARM` images for some older versions of the SDK platforms
- Open Andriod Virtual Device(AVD) Manager and configure and create a new virtual device with image files that run the same version as the development SDK
  - Cold Boot is a Boot Option that will clear the device memory, it is better for debug but it will be slower than Quick Boot

#### GenyMotion

- It provides many more virtual devices images.
- Sign Up, Download and Install [GenyMotion](https://www.genymotion.com).
  - It requries Virtual Box.
- Open `GenyMotion`, select, create and run a virtual device.
- In Android Studio's preferrence page, select `Plugins`, search and install the `Genymotion` plugin, restart Android Studio.
- Run the app by clicking the play button and select the `Genymotion` virtual device.

#### Physical Devices

- To show the screen of a physical device on the display.Install `Vysor` as an extension for Chrome, unlock the device and connect the device to the computer, open `Vysor` and click find device.
- On the phone, click the build number in the about page for 7 times to enable the `Developer options` menu for the physical device.
  - `USB debugging` option in the `Developer options` menu should be checked in order to run app on a real device for testing.
  - Click the play button in Andriod Studio and select the connected real device to build and run the app during development.

## Coding

- In an Android app, Java code is used to construct logic, XML is used to describe the layout and preference, Gradle is used to manage dependencies
- An Android project folder has a `java` folder, :
- `XML` Structure
  - `XML` files may start with `<?xml version="1.0" encoding="utf-8"?>` on the first line to describe the file version and encoding startard
  - Then the `XML` file has the other element that supplies information, different element name provides different information
    - E.g. `manifest` element is the parent element for the manifest file, a layout type element is the parent element for the layout file etc.
  - All elements have attributes like in `namespace:property="value"` format, where all parent element in the `XML` file starts with namespace `xmlns` (XML NameSpace)
    - e.g. `xmlnm:android="http://schemas.android.com/apk/res/android"
  - Once a property is defined in the parent element, it can be used as a namespace to access and define its properties
  - Certain element might have other attributes
  - Like any markup language, the element can be self closing or it can surround another element
  - It can contain variables or reference that start with `@` symbol
  - Inline comment: `<!-- Comment -->`
- The system performs basic scaling and resizing to adapt your user interface to different screens by using `dp` units, aka density-independent pixels
  - conversion of dp units to screen pixels `px = dp * (dpi / 160)`
  - Available units are: px (pixels), dp (density-independent pixels), sp (scaled pixels based on preferred font size), in (inches), and mm (millimeters)

### `java` folder

- It can access variables or reference that imported from `R`
- Values from `strings.xml` can be loaded using `getString()`, e.g. `String name = getString(R.string.name)`
  - use `getResources().getStringArray(R.array.weekdays);` to load arrays
- `onCreate()` is called once during app launch or after orientation of the app is changed
  - All code for initialization and should be placed here
  - Variables can be declared at the top inside the class as `private ClassName var;`, but they need to be initialized inside `onCreate()`

#### Activities

- In an android app, each page is called an activity
- The main activity is the first screen to appear when the user launches the app
- Each activity is only loosely bound to the other activities
- Only one activity can have focus and be responding to events from the user such as touch events
- Each activity is a customized class in the Java code
- like programming paradigms in which apps are launched with a main() method, the
- Android system initiates code in an Activity instance by invoking specific callback methods that correspond to specific stages of its lifecycle, in a order from top to bottom:
  - `onCreate()` - invoked when the app is initiately loaded or rotated, it can be used to do initialization
  - `onStart()` - invoked after `onCreate()` or `onRestart()`, right before the activity become visible
  - `onResume()` - invoked after `onStart()` or `onPause()`, right after the activity become visible
  - `onPause()` - invoked when the activity is partially hidden, hidden, or goes out of focus, it can be used to save user data
    - invoke `onResume()` if user returns to the activity before it is completely hidden
  - `onStop()` - invoked after the new activity is completely back to alive
    - `onRestart()` - invoked when user navigates back to the activity after `onStop()` is called before destroyed by the system
  - `onDestroy()` stopping the app or activity being destroyed by the system
    - This method is not guaranteed to be called, it highly rely on the decision of the system(e.g. low memory)
- Navigate from one activity to another is actually add a new activity to the top of a stack,
  - all activities in the stack is stored in the memory
  - the phone’s back button can return to the previous activity with `onResume()`, the top activity might be destroyed if memory is low

#### Event Handler

- `onClick()`, this handler can be overridden and get the trigger widget(widget that is being clicked) from the argument. it takes any view objects. e.g. `public void onClick(View view) {}`
  - use `Button bview = (Button) view;` to access the button object that is being clicked
- Optionally, Implement various listeners and bind then to local handler function, instead of using layout attribute setting
  - `implements View.OnClickListener` for the activity class, then find the button `Button bview = findViewById(R.id.button1);`, and bind local handler to the button's `OnClickListener`, `bview.setOnClickListener(this);`
  - Listeners interface:
    - `View.OnClickListener` has the `onClick()` method
    - `AdapterView.OnItemSelectedListener` has the `onItemSelected()` method
  - Optionally use, `widgetObject.listenerType(this::handlerMethod)` to bind in the `onCreate()` method without implement the linstener interface for the activity class
    - It works when listener interface requires overriding one method
  - `this::handlerMethod` can be replace by anonymous classes as
    ```java
    buttonView.setOnClickListener(new View.OnClickListener() {
      @Override
      public void onClick(View view) {
        Log.d(tag,"Button Pressed");
      }
    });
    ```
    - Anonymous classes protect the privacy of the method minimizing the class interface, but does not help with readability
  - A handler can be written in the acivity class as a separate method as `public void handlerName(View view) {}`
  - It must return `void`(or have no return) and it must take a single argument of type `View`
  - The handler can be assigned to a widget in the attribute panel of the layout desinger

#### Fragments

- One or more layout classes can be added to an activity as a sub view
- The same code can be designed to work on two devices with different fragment layouts
- Widgets inside fragment can be access after `onStart()`
- Fragments have a lifecycle similar to the activity lifecycle
  - fragment is created within the `setContentView()` of the activity class, if it it dragged into the main activity `xml`
  - fragment resumes after the parent activity is resumed
  - fragment will be destroyed when the activity is destroyed
- Before creation `onCreate()` is called
- During initialization `onCreateView()`, `onViewCreated()` are called in sequence
- After creation `onViewStateRestored()` is called
- After started `onStart()` is called
- Before fragment become active `onResume()` is called
- When fragment or parent activity loses focus, `onPause()` is called
- After completely back to alive `onStop()` is called
- After stopping, `onSaveInstanceState()` is called
- Before destroy `onDestoryView()` is called
- During destroy `onDestroy()` is called

##### Fragment Manager

- FragmentManager is the class responsible for performing actions on your app's fragments
- At runtime, A FragmentManager can add, remove, replace, and perform other actions with fragments in response to user interaction
- Each action is called a transcation and multiple transctions can have a single committed
- final call on each FragmentTransaction must commit the transaction
- For example:
  ```java
  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    FragmentManager fm = getSupportFragmentManager();
    FragmentTransaction fragmentTransaction = fm.beginTransaction();
    // Create a new instance of our Fragment class
    Fragment myFragment1 = new BlankFragment();
    // replace the fragment instance into a frame (viewgroup) in our layout.
    fragmentTransaction.replace(R.id.frame2, myFragment1);
    fragmentTransaction.commit();
  }
  ```

#### View object

- View object class represents the basic building block for user interface components. A View occupies a rectangular area on the screen and is responsiblefor drawing and event handling. View is the base class for widgets, which are used to create interactive UI components (buttons, text fields, etc.)
- View objects can be obtained using `findViewById` with element id, `View myView = (View) findViewById(R.id.elementID)`
  - returns `null` if element ID is not found in the layout xml
  - Explicit Casting is optional
- Use `view.getId()` to get the id of any view object
- `view.setImageResource(R.drawable.image_name);` change image

#### Intent object

- It is used to naigate between activities
- `Intent switch2Activity2 = new Intent(MainActivity.this, MainActivity2.class);` declares new intent, it takes the class of each imported activity files as arguments
- `startActivity(switch2Activity2);` navigate to the second activity
- `switch2Activity2.putExtra("data", "Hello");` use intent to store string into varialbe name `"data"`
- In any `onCreate()` method, use `Intent intent = getIntent();` to access the intent that started it
- Use `String i = intent.getStringExtra("data");` to get values stored in intent

#### Application Context

- The Context class provides an interface to global information about an application environment
- This is an abstract class whose implementation is provided by the Android system
- It allows access to application-specific resources and classes, as well as up-calls for application-level operations such as launching activities, broadcasting and receiving intents, etc

##### Shared Preferences

- The Shared Preferences file is accessed through the application context
- It collects data which can be used to store state information about an application that persists between application restarts
- Shared Preferences provides an interface for accessing and modifying preference data returned by `getSharedPreferences()`
- For any particular set of preferences, there is a single instance of this class that all clients share.
  Modifications to the preferences must go through an Editor object to ensure the preference values remain in a consistent state and control when they are committed to storage
- Objects that are returned from the various get methods must be treated as immutable by the application
- This class provides strong consistency guarantees.
  - It uses expensive operations which might slow down an app
- load our app state when the app starts up, and save the state when it pauses
- The getSharedPreferences method retrieves and hold the contents of the preferences file, returning a SharedPreferences through which you can retrieve and modify its values
  - Only one instance of the SharedPreferences object is returned to any callers for the same name, meaning they will see each other's edits as soon as they are made.
- If the preferences directory does not already exist, it will be created when this method is called
- Fetch the string that stored our saved state from the `onResume()` state, just before the app becomes active
  ```java
  @Override
  public void onResume(){
    super.onResume();
    SharedPreferences sharedPreferences = this.getSharedPreferences("PREFERENCE_NAME", Context.MODE_PRIVATE);
    // There are also getAll(), getInt(), getFloat(), getBoolean(), getLong(), getStringSet(), contains("TAG")
    String switchText = sharedPreferences.getString("TAG", "default value");
  ```
- Save the app state as soon as we go into the `onPause()` state
  ```java
  @Override
  public void onPause() {
    super.onPause();
    SharedPreferences.Editor editor = sharedPreferences.edit();
    // There are also putInt(), putFloat(), putBoolean(), putLong(), putStringSet(), remove("TAG"), clear()
    editor.putString("TAG", "new_value");
    editor.apply();
  }
  ```

#### Formatter

##### Simple Date Format

```java
SimpleDateFormat formatter = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
Date date = new Date();
String formattedText = "Formatted as: " + formatter.format(date);
```

#### TextView

- it is a object class inherits all the methods of the View Object. It provides a basic element for display to the user
- `TextView myTextView = (TextView) findViewById(R.id.elementID)`
- `myTextView.setText("Hello")`, set text

#### EditText

- it is a object class that inherits the methods of the TextView object. It provides an element that allows input.
- `EditText myEditText = (EditText) findViewById(R.id.elementID)`
- `myEditText.getText().toString()`, returns the string value of the current edittext input box
  - `getText()` returns a `Editable` instance can be converted to string using `toString()`

#### Spinner

- `Spinner mySpinner = findViewById(R.id.spinner);`
- Spinner requires to override two different methods
  - `onItemSelected(AdapterView<?> parent, View view, int position, long id)` Callback method to be invoked when a new item in this view has been selected. It is not called if there is no change in selection
  - `onNothingSelected(AdapterView<?> parent)` Callback method to be invoked when the selection disappears from this view or when the adapter becomes empty
- `mySpinner.setSelection(0, false);` set the first selection as default
  - Set a selection before setting listener, to prevent "ghost" selection on start

#### Button

- Example Handler for Switch as onClick attribute:
  ```java
  public void handlerName(View view) {
    Button bview = (Button) view;
    bview.getId()
  }
  ```

#### Switch

- The switch class inherits from the button class
- It also has an onClick attribute in XML which can be used to specify a handler
- Example Handler for Switch as onClick attribute:
  ```java
  public void handlerName(View view) {
    Switch sview = (Switch) view;
    if (sview.isChecked()) {
      switchText = "ON @ " + formatter.format(date);;
    }
  }
  ```

### `manifests` folder

#### `AndroidManifest.xml`

- Every app project must have an `AndroidManifest.xml` file at the root of the `manifests` folder
- It contains the essential information about the project
  - The app's package name, which usually matches your code's namespace.
    - The Android build tools use this to determine the location of code entities when building your project
  - The components of the app, which include all activities, services, broadcast receivers, and content providers.
    - Each component must define basic properties such as the name of its Kotlin or Java class
  - The permissions that the app needs in order to access protected parts of thesystem or other apps
  - The hardware and software features the app requires, which affects which devices can install the app from Google Play

##### Application Element

- `android:allowBackupWhether="true"` to allow the application to participate in the backup and restore infrastructure.
  - If this attribute is set to `"false"`, no backup or restore of the applicationwill ever be performed
- `android:icon="@mipmap/ic_launcher"` path to the icons folders
  - the `"@"` syntax provides an XML reference to an internal resource
- `android:roundIcon="@mipmap/ic_launcher_round"` path to the round icons folders
- `android:theme` A reference to a style resource defining a default theme for all activities in the application
  - A style is a collection of attributes that specify the appearance for a single View.
  - A theme is a collection of attributes that's applied to an entire app, activity, or view hierarchy
  - Themes can also apply styles to non-view elements, such as the status bar and window background

##### Activity Element

- declares an activity (an Activity subclass) that implements part of the application's visual user interface
- All activities must be represented by `<activity>` elements in the manifest file
- Any that are not declared there will not be seen by the system and will never be run
- `android:name=".MainActivity"` The name attribute defines the class that implements the activity
- `<intent-filter><action android:name="android.intent.action.MAIN" /><category android:name="android.intent.category.LAUNCHER" /></intent-filter>` It declares main activity

### `res` folder

- It contains all the app resources

#### `layout` folder

- A `XML` layout file uses the following layout type as parent element to define layouts
- Element will be moved to top left corner if no layout constraint is defined
- Common attributes
  - `android:background=“#ffffff”` set the background
  - `android:layout_width`, `android:layout_height` the width and height of the layout container, its value can be:
    - `"match_parent"` set it to be the same as its parent
    - `"wrap_content"` set it to be the same as its content
  - `android:id="@+id/key"` set element id as `key`, it is used as reference to the element by the Java code
- Common elements
  - `<Button />`
    - `android:text="Hello"`
    - `android:textColor="#fff"`

##### Layout Types

- `<LinearLayout>`
  - It defines layout container that can grow in two direction, either vertical or horizontal
  - `android:orientation` can be either `"vertical"` or `"horizontal"`
  - `android:layout_weight` controls how much space it takes
    - set `android:layout_height`(when vertical) or `android:layout_height`(when horizontal) to `0dp` and `android:layout_weight` to `1` can make all component evenly distributes with zero space in between
- `<RelativeLayout>`
  - It defines elements relative to others(legacy)
  - `android:layout_centerHorizontal="true"`, `android:layout_centerVertical="true"`, `android:layout_centerInParent="true"` for centering elements
- `<ConstraintLayout>`
  - It defines elements relative to others
- `<FrameLayout>` it is designed to block out an area on the screen

##### Elements

- PlainText
  - `backgroudTint` controlls the underline color
- EditText
  - Used to get user input, can have different types, e.g. `android:inputType="number"` for input number only
    - can drag different types of EditText from the palette
- Spinner
  - spinner can present a collection of menu items
  - It takes an array as entries
- Switch
  - The switch has a default state, the attribute is named "checked", set it to true.

#### `drawable` folder

- It stores all images for the app
- To use a bitmap file, copy a file into this directory
- There are also XML formats that specify drawable resources
- It can be accessed by Java code using `R.drawable.image_name`
- Images can be defined using `XML` as well,`app > res > drawable` and right-click, select`New > Drawable resource file`, and add vector definition like the following:
  ```xml
  <selector xmlns:android="http://schemas.android.com/apk/res/android"> <item>
      <shape> <gradient
          android:startColor="#89cbee" android:endColor="#004F81" android:angle="270" />
          <stroke
              android:width="1dp" android:color="#4aa5d4" />
          <corners android:radius="7dp" />
          <padding android:left="10dp" android:top="10dp" android:right="10dp" android:bottom="10dp" />
      </shape> </item>
  </selector>
  ```

#### `minmap` folder

- It stores the app icon file
- The image files spec can be found [here](https://developer.android.com/training/multiscreen/screendensities).
- It can has two folder one contains square app icons, the other one contains round app icons.
- Images can be resize and organize by the [Java Final Resizer](https://github.com/asystat/Final-Android-Resizer).
  - When images have been resized, copy and paste the output image directly to the `res` folder

#### `values` folder

##### `themes/themes.xml`

- change the parent attribute of the style element to change the app bar style
- `colorPrimary` controls the app bar color
- `colorPrimaryVariant` controls the status bar color
- The background color of some widgets is controlled by the theme type

##### `strings.xml`

- It stores all the hardcoded strings
- The file has parent element `<resources></resources>`
- It consisted of multiple sting records as `<string name="key">value</string>`
- It can stores arrays as `<string-array name="key"><item>A</item><item>B</item><item>C</item></string-array>`
- It can be used in Java code as `R.string.string_name`
- It can be used in XML code or the layout attribute panel as `@string/string_name`

## Gradle Scripts

- Each app is associated with a group of gradle scripts
- Gradle is an advanced build toolkit, to automate and manage the build process, while allowing you to define flexible custom build configurations
- Gradle and the Android plugin run independent of Android Studio. This means Android apps can be built either from within Android Studio or use the command lineon your machine, or on machines where Android Studio is not installed (such as continuous integration servers)
- Android studio will automatically manage the dependencies
  - sometimes we will need to tweak dependencies to ensure that certain widgets are working
  - Build errors that complain about missing components are sometimes the result of missing dependencies

## Android Studio IDE

- Ultimately, all editors will change either the `.xml` code or the `.java` code
- Differenct code uses different editor
- To format code, press `Command+Option+L` on Mac, `CTRL+ALT+L` on Windows

### App Directory

- Right click on the root of the app tree and create a new `Empty Activity`
- Right click on the project file tree, select `New Fragment`, and `Blank` fragment
  - This will create a new layout file and it will also create a Java file with some fundamental fragment methods

### Java Editor

- press `option + Enter` to auto import library

### XML Editor

- Hold `Alt` or `Option` and click on namespace name to auto import
- Changes made to the `XML` layout file will be immeditately rendered in the preview of the Design Editor
- Right click `res` folder and open the `Image Asset`, this tool can be used to generate icons for the app

### Layout Editor

- The Layout Editor enables you to quickly build layouts by dragging UI elements around a visual design editor instead of writing layout XML by hand
- The Layout Editor appears when opening an `XML` layout file

#### Palette

- Contains various views and view groups that you can drag into your layout
- After files for fragment is created, the layout widget is available under `Common Views` and is ready to be dragged into the layout editor

#### Component Tree

- Shows the hierarchy of components in your layout
- Right click a layout element inside the component tree, `Convert view...` can convert between different layout types
- Right click on `LinearLayout` in the component tree, from the first item select `convert orientation` to vonvert layout between vertical and horizontal(default)

#### Toolbar

- Click these buttons to configure your layout appearance in the editor and change layout attributes.
- Infer Constraint button can auto create relative constraint
- There is a `Clear All Constraints` button
- Use `eye` tool to select `Show All constraints`

#### Design Editor

- Edit layout in Design view, Blueprint view, or both
- The design editor can preview your layout on different Android devices and versions, and you can dynamically resize the layout to be sure it works well on different screen sizes
- Element and layout can be dragged into the Design Editor from the palette or component tree
- After dragging `ImageView` into the layout select the image in the resources directory to import
  - The `tools:srcCompat` attr sets the image for the editor,

#### Blueprint View

- It is good for construct constraints for layout
- Drag the point on an element to other reference to establish constraints
- `WM` wiggle lines means match constraints, flexiable
- `>>` lines means Wrap Content
- `|--|` lines means fixed
- `WM-|->` lines means flexiale constraint with a fixed minimum constraint
- If a element is surrounded by match constraints, it will be centered
- A group of widgets can be chained(evenly spaced) or aligned in the right click menu
- A guideline can be added from the top menu bar, it can be used as reference when setting up constraints for widgets
  - guideline can be constrained by a fixed amount to the top or the bottom and also as a percentage

#### Attributes

- Controls for the selected view's attributes
- Layout elements and be controlled and set by using the right attributes panel
- The constraint widget in the attributes tool will allow you to enter specific numbers
- Right click to show other reference like a baseline of an element and drag it around to create constraint
- View id can be changed at the top
  - It has to be unique
- It can be used to assign handler to an action of an element

#### View mode

- View layout in either Code code mode icon, Design design mode icon, or Split split mode icon modes. Split mode shows both the Code and Design windows at the same time.

#### Zoom and pan controls

- Control the preview size and position within the editor.

## Debug

- Click the bug icon to debug the app and see error messages in the Logcat console at the bottom
- User `Log.d()` to print output and view them in Logcat tab at the bottom of android studio
  - Usually and tag can be used to filter the logs, `final static String tag = "==LIFECYCLE==";` , `Log.d(tag, "Debug");`

## Exporting Projects

- a `.zip` file of the project can be created using the option under `Manage IDE Settings --> Export to Zip File...`
