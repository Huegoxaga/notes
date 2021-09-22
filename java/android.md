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
- Emulator side menu
  - rotate the device
  - change the device location

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
    - e.g. `xmlnm:android="http://schemas.android.com/apk/res/android"`
  - Once a property is defined in the parent element, it can be used as a namespace to access and define its properties
  - Certain element might have other attributes
  - Like any markup language, the element can be self closing or it can surround another element
  - It can contain variables or reference that start with `@` symbol
  - Inline comment: `<!-- Comment -->`
- The system performs basic scaling and resizing to adapt your user interface to different screens by using `dp` units, aka density-independent pixels
  - conversion of dp units to screen pixels `px = dp * (dpi / 160)`
  - Available units are: `px` (pixels), `dp` (density-independent pixels), `sp` (scaled pixels based on preferred font size), `in` (inches), and `mm` (millimeters)
- Avoid casting as much as possible

### `java` folder

- It can access variables or reference that imported from `R`
- Values from `strings.xml` can be loaded using `getString()`, e.g. `String name = getString(R.string.name)` or `getString(R.string.hello, "Variable One", "Variable Two");`
  - use `getResources().getStringArray(R.array.weekdays);` to load arrays
- `onCreate()` is called once during app launch or after orientation of the app is changed
  - All code for initialization and should be placed here
  - Variables can be declared at the top inside the class as `private ClassName var;`, but they need to be initialized inside `onCreate()`
- check and ask for permissions
  ```java
  if (ActivityCompat.checkSelfPermission(this, Manifest.permission.RECEIVE_SMS) != PackageManager.PERMISSION_GRANTED) {
    ActivityCompat.requestPermissions(this,new String[]{Manifest.permission.RECEIVE_SMS}, 1);
  }
  ```
  - The request is asynchronous, so you can't confirm immediately whether or not it was granted, therefore a callback can be used
  - The `1` in the `requestPermissions()` parameter is the result code reported to permission result callback, should be >= 0
  - `onRequestPermissionsResult()` will be invoked whenever a permission is granted
  ```java
    @Override
    public void onRequestPermissionsResult(int resultCode, String permissions[], int[] results ) {
    switch (resultCode) {
      case 1:
        if (results.length > 0 && results[0] == PackageManager.PERMISSION_GRANTED) {
          // initialize permission dependent service here
        }
    }
  }
  ```
  - For security reason, multiple popups are not allowed
  - The security issue involves attempting to confuse a user by asking for permissions, but hiding the exact message with another overlay
- Inflater should be used when loading a layout during runtime
  - One inflate call can only load one `.xml` file

#### Activities

- In an android app, each page is called an activity
- The main activity is the first screen to appear when the user launches the app
- Each activity is only loosely bound to the other activities
- It extends from Context class
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
- If this activity has no `setContentView()` and ends with `finish()` it will not inflate any layout
- Before `setContentView()`, `getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN, WindowManager.LayoutParams.FLAG_FULLSCREEN);` can be used to hide the status bar
- Declare `private static Activity currentActivity = null;` in the activity class and assign `currentActivity = this;` in the `onCreate()` method so the current state of the acivity can be accessed by other classes using a public getter at runtime

#### Event Handler

- `onClick()`, this handler can be overridden and get the trigger widget(widget that is being clicked) from the argument. it takes any view objects. e.g. `public void onClick(View view) {}`
  - use `Button bview = (Button) view;` to access the button object that is being clicked
- Optionally, Implement various listeners and bind then to local handler function, instead of using layout attribute setting
  - `implements View.OnClickListener` for the activity class, then find the button `Button bview = findViewById(R.id.button1);`, and bind local handler to the button's `OnClickListener`, `bview.setOnClickListener(this);`
  - Listeners interface:
    - `View.OnClickListener` has the `onClick()` method
    - `AdapterView.OnItemSelectedListener` has `onItemSelected()` and `onNothingSelected()` methods
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
  - fragment is created within the `setContentView()` of the activity class, if it is dragged into the main activity `xml`
  - fragment resumes after the parent activity is resumed
  - fragment will be destroyed when the activity is destroyed or replaced by another fragment
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
    // Remove a fragment
    // fragmentTransaction.remove(R.id.frame2);
    fragmentTransaction.commit();
  }
  ```
- Main Activity can get `getSupportFragmentManager()` when it extends the `AppCompatActivity` interface
  - `AppCompatActivity` extends `FragmentActivity`
  - optionally, `getFragmentManager()` method is available for fragment classes and is part of an older API, and deprecated in API level 28, it's replaced by `getParentFragmentManager()`
- Fragment constructor - can be used to pass view into framgment class when initialized with fragment manager. For example when use fragment manager in the main acticity, declare fragment as `Fragment myFragment1 = new BlankFragment(findViewById(R.id.textview));`
  ```java
  // Define constructor inside fragment class
  public BlankFragment(TextView tview) {
  this.tview = tview;
  }
  // then tview.findViewById() can be accessed globally in the fragment class
  ```
- `getActivity()` can also be used to get reference of a widget from parent activity
  - From the fragments uses `Switch actSw = getActivity().findViewById(R.id.switch1);`
  - It was added in API level 11, but then deprecated in API level 28
  - Similar to `getActivity()`, `requireActivity()` is safer to use because it will always return a valid non-null activity

##### LayoutInflater

- Fragments use inflater to create views
- `LayoutInflater` is used to create a new View (or Layout) object from xml layouts
- Use `View myview = inflater.inflate(R.layout.fragment_custom, parent, false);` to create the view, the view will be inflated with the given parent, but won't attach it to the parent
  - `infalInflater.inflate(R.layout.list_item, null);` this method is not recommanded

##### Event Handlers for Widgets inside a Fragment

- Binding Listener in fragment class, in `onCreateView()` fragment view is returned from the inflater
  ```java
  @Override
  public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
    View fragView = inflater.inflate(R.layout.fragment_blank, container, false);
    Switch sview = fragView.findViewById(R.id.switch1);
    sview.setOnClickListener(this::handlerName);
    return fragView;
  }
  ```
- Binding Listener in main class's `onCreate()` method if the fragment is embedded directly in the XML instead of using fragment manager
  ```java
  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    View fragView = findViewById(R.id.fragment);
    Switch sview = fragView.findViewById(R.id.switch1);
    sview.setOnClickListener(this::onSwitch);
  }
  ```

##### DialogFragment

- It is a type of Fragment that works as a dialog
- All element should be `wrap_content` and with min width, `match_parent` won't work for dialog fragments
- Android Studio does not have create DialogFragment option, create an Empty Fragment and replace the class with the following
  ```java
  /**
  * For a Dialog we must extend the DialogFragment Class
  * We implement OnClickListener to handle button click events
  */
  public class CustomDialog extends DialogFragment implements View.OnClickListener {
    public CustomDialog() {
      // Required empty public constructor
    }
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
      // Inflate the layout for this fragment
      // We saved the inflated layout in our myview variable
      View myview = inflater.inflate(R.layout.fragment_custom, container, false);
      // Attach the OnClickListener to the button
      Button button = myview.findViewById(R.id.dialogbutton);
      button.setOnClickListener(this);
      return myview;
    }
    @Override
    public void onClick(View v) {
      // Get the string out of our Edit field
      // getView() will return the view of the current Fragment
      EditText editInput = getView().findViewById(R.id.dialogedit);
      String myInput = editInput.getText().toString();
      // get the main activity object
      MainActivity main = (MainActivity) getActivity();
      // call a method in the main activity class
      main.sendInput(myInput);
      // Dismiss will close the dialog
      dismiss();
      }
    }
  ```
- In the example `sendInput` is a user defined method in the main class as `public void sendInput(String in) { }`
- Use `CustomDialog myDialog = new CustomDialog();`, `myDialog.show(getSupportFragmentManager(),null);` to initiate and show the dialog in main class

#### Application Class

- The Application class in Android is the base class within an Android app that contains all other components such as activities and services
- It is instantiated before any other class
- This class is primarily used for initialization of global state before the first Activity is displayed
- See the following template for custom application classes

```java
import android.app.Application;

public class MyCustomApplication extends Application {
  // Called when the application is starting, before any other application objects have been created.
  // Overriding this method is totally optional!
  @Override
  public void onCreate() {
    super.onCreate();
    // Required initialization logic here!
    }
    // Called by the system when the device configuration changes while your component is running.
    // Overriding this method is totally optional!
  @Override
  public void onConfigurationChanged(Configuration newConfig) {
    super.onConfigurationChanged(newConfig);
  }
  // This is called when the overall system is running low on memory,
  // and would like actively running processes to tighten their belts.
  // Overriding this method is totally optional!
  @Override
  public void onLowMemory() {
    super.onLowMemory();
  }
}
```

#### View

- View object class represents the basic building block for user interface components. A View occupies a rectangular area on the screen and is responsiblefor drawing and event handling. View is the base class for widgets, which are used to create interactive UI components (buttons, text fields, etc.)
- View objects can be obtained using `findViewById` with element id, `View myView = (View) findViewById(R.id.elementID)`
  - returns `null` if element ID is not found in the layout xml
  - Explicit Casting is optional
- Use `view.getId()` to get the id of any view object
  - Is it good for comparison, e.g. `view.getId() == R.id.button`
- `view.setImageResource(R.drawable.image_name);` change image
- `view.setVisibility(View.GONE);` hide the view, and it doesn't take any space for layout purposes
- `view.setVisibility(View.INVISIBLE);` hide the view, but it still takes up space for layout purposes
- `view.setVisibility(View.VISIBLE);` show the view
- `getView()` can be used to return the view object of the class it belongs to, after `onCreate` or `onCreateView`is invoked
- `view.setSystemUiVisibility(View.SYSTEM_UI_FLAG_LOW_PROFILE | View.SYSTEM_UI_FLAG_FULLSCREEN | View.SYSTEM_UI_FLAG_LAYOUT_STABLE | View.SYSTEM_UI_FLAG_IMMERSIVE_STICKY | View.SYSTEM_UI_FLAG_LAYOUT_HIDE_NAVIGATION | View.SYSTEM_UI_FLAG_HIDE_NAVIGATION);` Set the view to fullscreen
- The layout of a view can be defined in `Java` as well:
  - `View myView = new View(context);`
  - `myView.setPadding(10, 10, 10, 10);`
- Nested scrollable views need to define height using code logic by overriding `onMeasure()` method in a custom view class as follows, the layout should have height as `wrap_content`

```java
@Override
protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
    int heightSpec;

    if (getLayoutParams().height == LayoutParams.WRAP_CONTENT) {

        // The two leftmost bits in the height measure spec have
        // a special meaning, hence we can't use them to describe height.
        heightSpec = MeasureSpec.makeMeasureSpec(
                Integer.MAX_VALUE >>2, MeasureSpec.AT_MOST);
    }
    else {
        // Any other height should be respected as is.
        heightSpec = heightMeasureSpec;
    }

    super.onMeasure(widthMeasureSpec, heightSpec);
}
```

#### ViewGroup

- It is the base class for `Layout`s

#### Intent

- It is used to navigate between activities
- `Intent switch2Activity2 = new Intent(MainActivity.this, MainActivity2.class);` declares new intent, it takes the class of each imported activity files as arguments
- `startActivity(switch2Activity2);` navigate to the second activity
- `switch2Activity2.putExtra("data", "Hello");` use intent to store string into varialbe name `"data"`
  - The variable name can be a constant from `Intent` class, e.g. `Intent.EXTRA_TEXT`
  - The size of the data cannot be larger than around `1M`, or the app will crash silently when new activity starts
- In any `onCreate()` method, use `Intent intent = getIntent();` to access the intent that started it
  - Use `if (getIntent()!=null && getIntent().hasExtra("DataName")) {}` to get if the intent has the data
- Use `String i = intent.getStringExtra("data");` to get a string value stored in intent
  - Use `intent.getIntExtra("increment", defaultValue);` and `intent.getBooleanExtra("reset", defaultValue);` or other data types
- Use `startActivityForResult(intent, requestCode);` to pass data, request code to the other activity
  - requestCode should be greater or equal than `0`
- `onActivityResult()` is called when returning from another activity with request/result code and intent object with data
  ```java
  @Override
  protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);
    // Get data from return intent
    data.getIntExtra("DEMO_DATA", 0));
  }
  ```
  - `resultCode` can be `RESULT_OK` or `RESULT_CANCELED`
  - All parent class's `onActivityResult()` will be invoke with the same return data
- Example handler for return button from the other activity class which initiate the return
  ```java
  public void onClickClose(View view) {
    Log.d(tag, "onClickClose()");
    Intent returnIntent = new Intent();
    returnIntent.putExtra("DEMO_DATA", 99);
    // set result code and returning intent with data
    setResult(RESULT_OK, returnIntent);
    finish();
    }
  ```
  - The result code will be `RESULT_CANCELED` if the activity explicitly returned that, didn't return any result, or crashed during its operation
    - Using back button will get `RESULT_CANCELED` as well
  - `onResume()` will be called after

#### Context Class

- The Context class provides an interface to global information about an application environment
  - `Activity` and `Application` class are inherited from `Context` class
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
- To store objects into shared preference, use `gson` library to convert Java object into json string then use `putString()`
- Fetch the string that stored our saved state from the `onResume()` state, just before the app becomes active
  ```java
  private SharedPreferences sharedPreferences;
  @Override
  public void onResume(){
    super.onResume();
    sharedPreferences = this.getSharedPreferences("PREFERENCE_NAME", Context.MODE_PRIVATE);
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
- The listener for EditText should be defined as follows

  ```java
  myEditText.addTextChangedListener(new TextWatcher() {
    public void afterTextChanged(Editable s) {
      Log.d("Changed Text: ", s.toString());
    }
    public void beforeTextChanged(CharSequence s, int start, int count, int after) {}
    public void onTextChanged(CharSequence s, int start, int before, int count) {}
  });
  ```

#### Spinner

- `Spinner mySpinner = findViewById(R.id.spinner);`
- The Listener for Spinner requires to override two different methods
  - `onItemSelected(AdapterView<?> parent, View view, int position, long id)` Callback method to be invoked when a new item in this view has been selected. It is not called if there is no change in selection
  - When item list increase from 0 to 1, that single item will not be able to selected, add a first item as `Select an Item` to avoid this issue
  - `onNothingSelected(AdapterView<?> parent)` Callback method to be invoked when the selection disappears from this view or when the adapter becomes empty
- It uses an adapter to pupolate its options, use `mySpinner.setAdapter(adapter);` to assign an adapter for the spinner
- `mySpinner.setSelection(0, false);` set the first selection as default
  - Set a selection before setting listener, to prevent "ghost" selection on start
  - It works after `setAdapter()`
- `mySpinner.getSelectedItemPosition()` return the index of seltected item, return `-1` if no item is selected

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
- use `switchObj.setChecked(false);` to set switch state
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

#### Toast

- A toast is a view containing a quick little message for the user. it appears as a floating view over the application. It will never receive focus
- `Toast.makeText(this, "Basic Toast", Toast.LENGTH_LONG).show();`
  - `Toast.LENGTH_LONG` specifies the amount of time the message is visible
- Use Toast to show a view during runtime
  ```java
  // To show a toast with a custom layout - need to inflate the layout
  LayoutInflater myinflator = getLayoutInflater();
  View customtoast = myinflator.inflate(R.layout.customlayout, null);
  // Now build the Toast - adjust settings
  Toast myToast = new Toast(this);
  // set the view duration
  myToast.setDuration(Toast.LENGTH_LONG);
  // position the toast at the top of the screen
  myToast.setGravity(Gravity.TOP, 0, 0);
  // set connect the custom layout (deprecated in API Level 30)
  myToast.setView( customtoast );
  // And finally show it
  myToast.show();
  ```
- When only Context is provided use `getSystemService()` to get the layout inflater
  ```java
  // To show a toast with a custom layout - need to inflate the layoutLayout
  LayoutInflater myLayout = (LayoutInflater) context.getSystemService(Context.LAYOUT_INFLATER_SERVICE);
  // optionally, LayoutInflater.from(context)
  View customtoast = myLayout.inflate(R.layout.message_output_layout, null);
  // Now build the Toast - adjust settings
  Toast myToast = new Toast(context);
  // set the view duration
  myToast.setDuration(Toast.LENGTH_LONG);
  // position the toast at the center of the screen
  myToast.setGravity(Gravity.CENTER, 0, 0);
  // set connect the custom layout (deprecated)
  myToast.setView(customtoast);
  // And finally show it
  myToast.show();
  ```

#### Snackbar

- It has some properties similar to toasts

#### Broadcast Receiver

- Receive broadcast information as subscriber
- Works in the background, as long as the permission is granted
  ```java
  public class MyReceiver extends BroadcastReceiver {
  public static String tag = "==MyReceiver==";
  @Override
  public void onReceive(Context context, Intent intent) {
    Log.d(tag, "onReceive"); }
    // get an array of messages if subscribe SMS
    SmsMessage[] messages = getMessagesFromIntent(intent);
    // Get the sender from the first message block
    String sender = messages[0].getOriginatingAddress();
    // Get the first message body text -
    String msg = messages[0].getMessageBody();
    // Launch main activity when a message is received
    Intent myIntent = new Intent(context, MainActivity.class);
    myIntent.putExtra(MSG, msg);
    // Set one or more New Activity Flags
    myIntent.addFlags( Intent.FLAG_ACTIVITY_CLEAR_TASK | Intent.FLAG_ACTIVITY_CLEAR_TOP |  Intent.FLAG_ACTIVITY_NEW_TASK);
    context.startActivity(myIntent);
    // Use getIntent(); in MainActivity to get data in putExtra()
  }
  ```
- Intent Flags
  - `FLAG_ACTIVITY_NEW_TASK` (must have)
    - This activity becomes the start of a new task on history stack.
  - `FLAG_ACTIVITY_CLEAR_TOP`
    - If the activity being launched is already running in the current task, then instead of launching a new instance of that activity, all of the other activities on top of it will be closed and this Intent will be delivered to the (now on top) old activity as a new Intent.
  - `FLAG_ACTIVITY_CLEAR_TASK` If set in an Intent passed to Context#startActivity, this flag will cause any existing task that would be associated with the activity to be cleared before the activity is started. This way, when you load that `FLAG_ACTIVITY_NEW_TASK`, and you hit the back button, you won't end up back at a login or sign up screen. That'd be a little awkward for our users if they were already logged in and hit it by accident.

#### Location Manager

- Add permission in manifest and initialize in `onRequestPermissionsResult()` in main if permission is granted
  ```java
  @Overridepublic void onRequestPermissionsResult(int resultCode, String permissions[], int[] results ) {
    Log.d(TAG, "onRequestPermissionsResult");
    switch (resultCode) {
      case 1:
        if (results.length > 0 && results[0] == PackageManager.PERMISSION_GRANTED) {
          LocationManager lm = (LocationManager) getSystemService(Context.LOCATION_SERVICE);
          // update every 5 seconds
          lm.requestLocationUpdates(LocationManager.GPS_PROVIDER,5000, 0, this);
          lm.requestLocationUpdates(LocationManager.NETWORK_PROVIDER,5000, 0, this);
        }
    }
  }
  ```
- Implementing the Location Listener
  ```java
  @Override
  public void onStatusChanged(String provider, int status, Bundle extras) {
    // get invoked once provider is changed to enabled or disabled
  }
  @Override
  public void onProviderEnabled(String provider) {
    // get invoked once provider is changed to enabled
  }
  @Override
  public void onProviderDisabled(String provider) {
    // get invoked once provider is changed to disabled
  }
  @Override
  public void onLocationChanged(Location location) {
    // Location Changed
    double loclat = location.getLatitude();
    double loclong = location.getLongitude();
    Toast.makeText(this, loclat + " : " + loclong, Toast.LENGTH_LONG).show();
    Log.d(TAG, "onRequestPermissionsResult");}
  ```

#### ListView

- Use ListView to display a string of array into a list

  ```java
  ArrayAdapter<String> adapter = new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1, myStringList);
  // get the number of elements
  Log.d(TAG, "adapter getCount() = " + adapter.getCount());
  ListView randList = findViewById(R.id.listView);
  // associate an adapter with the list
  randList.setAdapter(adapter);
  ```

- Adapter methods:
  - `adapter.add(data)` add a new data element to the existing adapter
- Predefined list item layout:
  - `android.R.layout.simple_list_item_1`
  - `android.R.layout.simple_list_item_2`
  - `android.R.layout.two_line_list_item`
- To handle items click, register the listener `randList.setOnItemClickListener(this::onItemClick);`, then define `public void onItemClick(AdapterView parent, View v, int position, long id) {}`
- Use the following way to add foot or header view to the list view

  ```java
  layoutInflater = getLayoutInflater();
  View footer = layoutInflater.inflate(R.layout.listview_footer, listView, false);
  listView.addFooterView(footer);
  listView.setAdapter(adapter);
  ```

##### BaseAdapter

- The class that can be overriden to define custom adapter for other views
- The following method need to be implemented for the `BaseAdapter` interface

```java
public class MyAdapter extends BaseAdapter {

    Context context;
    LayoutInflater layoutInflater;
    String[] data = { "A", "B", "C", "D", "E", "F", "G" };

    // define input data
    public MyAdapter(Context context) {
        this.context = context;
    }

    //define list length
    @Override
    public int getCount() {
        return data.length ;
    }
    //define items' position
    @Override
    public Object getItem(int position) {
        return data[position];
    }
    //defines item id
    @Override
    public long getItemId(int position) {
        return position;
    }
    //define view for each list cell
    @Override
    public View getView(int position, View view, ViewGroup parent) {
        if (view == null) {
          LayoutInflater layoutInflater = LayoutInflater.from(context);
          view = layoutInflater.inflate(R.layout.my_custom_layout, parent, false);
        }
        TextView title = view.findViewById(R.id.title);
        title.setText(data[position]);
        view.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(context, "Title: " + title.getText(), Toast.LENGTH_SHORT).show();

            }
        });
        return view;
    }
}
```

- In the view class, declear an instance of the adapter and use `listView.setadapter(myAdapter)` to inflat its content

#### AsyncTask

- It is good for running short operations in the background in a non-blocking manner
- It also forces serialization, so that only one AsyncTask runs at a time
- AsyncTask class definition
  ```java
  public class TestAsyncTask extends AsyncTask<String, Void, String> {
    public static final String TAG = "==TestAsynchTask==";
    /**
    * Called as soon as asynch tasks starts.
    */
    @Override
    protected void onPreExecute() {
      super.onPreExecute();
      Log.d(TAG,"onPreExectue");
    }
    /**
    * Called when asynch task finishes. Prints the result.
    * @param result string passed in from background task.
    */
    @Override
    protected void onPostExecute(String result) {
      super.onPostExecute(result);
      Log.d(TAG, result);
    }
    /**
    * Runs in a nonblocking background thread for you.
    * @param string parameters passed in from execute
    * @return value sent back to onPostExecute()
    */
    @Override
    protected String doInBackground(String... strings) {
      MainActivity.taskFunction("Asynch", strings[0]);
      String result = "Finished Job\n";
      for (String s : strings) {
        result += s + "\n";
      }
      return result;
    }
  }
  ```
- Run async task in `MainActivity.java`
  ```java
    // Start Async Background Thread, pass parameters
    TestAsyncTask dl = new TestAsyncTask();
    dl.execute("parameterA", "parameterB", "parameterC");
  }
  ```
- Example async task for download data from APIs
  ```java
  public class DownloadAsyncTask extends AsyncTask<String, Void, String> {
    public static final String TAG = "==MainActivity==";
    /**
      * Download data from the supplied URL, catch exceptions
      * @param params - first parameter is the URL
      * @return a string that concatenates all of the output together, null on failure
      */
    @Override
    protected String doInBackground(String... params) {
      Log.d(TAG, "Starting Background Task");
      StringBuilder results = new StringBuilder();
      try {
        URL url = new URL(params[0]);
        String line = null;
        // Open the Connection - GET is the default setRequestMethod
        HttpURLConnection conn = (HttpURLConnection) url.openConnection();
        // Read the response
        int statusCode = conn.getResponseCode();
        if (statusCode == 200) {
          InputStream inputStream = new BufferedInputStream(conn.getInputStream());                BufferedReader bufferedReader =new BufferedReader(new InputStreamReader(inputStream,"UTF-8"));while ((line = bufferedReader.readLine()) != null) {
            results.append(line);
            }
          }
          Log.d(TAG, "Data received = " + results.length());
          Log.d(TAG, "Response Code: " + statusCode);
        } catch (IOException ex) {
          Log.d(TAG, "Caught Exception: " + ex);
        }
        return results.toString();
      }
      /**
        * called after doInBackground completes
        * After download has completed associate, parse results, update view
        * @param result - do nothing if results == null
        */
      protected void onPostExecute(String result) {
        FairList fairlist = null;
        if (result == null) {
          Log.d(TAG, "no results");
        } else {
          Gson gson = new Gson();
          fairlist = gson.fromJson(result, FairList.class);
        }
        // fetch the current activity so we can lookup the ListView
        Activity currentActivity = MainActivity.getCurrentActivity();
        ListView lv = currentActivity.findViewById(R.id.listView);
        if (fairlist != null) {
          // if we populated fairlist then connect the adapter
          ArrayAdapter<Projects> adapter =new ArrayAdapter<Projects> (currentActivity, android.R.layout.simple_list_item_1, fairlist);
          lv.setAdapter(adapter);
        } else {
          // clear the list
          lv.setAdapter(null);
        }
      }
  ```

#### Handler

- Android handles all the UI events from one single thread called the Main or UI thread
- Handler is used often because, one cannot touch anything in the UI thread from a background thread
- Handler enables the use of another thread by communicating the `Message` or `Runnable` objects with the Main UI thread
  - `Runnable` is an interface in Java which initiate task in a new thread, it has a `run()` method which will be executed in a separate thread
- It is used to schedule a runnable task or send a delay messages by using one of the following methods:
  - `post(myRunnable)`, `myRunnable` is a `Runnable` object
  - `postAtTime(myRunnable, absUpTime)`
  - `postDelayed(myRunnable, delayInMS)`
  - `sendEmptyMessage(intMsgData)`, It sends a message containing only an int value from the parameter
  - `sendMessage(myMessage)`, `myMessage` is a `Message` object
  - `sendMessageAtTime(myMessage, absUpTime)`
  - `sendMessageDelayed(myMessage, delayInMS)`
  - `removeCallbacks(myRunnable)` Cancel all delayed runnable in queue
- To run a runnable in a short delay:

  ```java
  private final Handler handler = new Handler();
  private final Runnable r = new Runnable() {
      @Override
      public void run() {
          // Tasks
      }
  };
  // run r in 1 second
  handler.postDelayed(r, 1000);
  ```

- To execute a message:

  ```java
  // in the background thread
  if(dataArrives){
      Message msg = handler.obtainMessage();
      msg.what = UPDATE_IMAGE;
      msg.obj = bitmap;
      msg.arg1 = index;
      handler.sendMessage(msg);
  }
  // in the UI thread
  final Handler handler = new Handler(){
    @Override
    public void handleMessage(Message msg) {
      if(msg.what==UPDATE_IMAGE){
        images.get(msg.arg1).setImageBitmap((Bitmap) msg.obj);
      }
      super.handleMessage(msg);
    }
  };
  ```

#### SQLiteOpenHelper

- A helper class to define, create, and update database schema with version management
  ```java
  public class MyDbHelper extends SQLiteOpenHelper {
    public static final String DATABASE_NAME = "MyDatabase.db";
    // version number of the database (starting at 1); if the database is older, onUpgrade(SQLiteDatabase, int, int) will be used to upgrade the database; if the database is newer, onDowngrade(SQLiteDatabase, int, int) will be used to downgrade the database.
    public static final int DATABASE_VERSION = 1;
    public static final String MYTABLE = "mytable";
    public static final String ID = "_id";
    public static final String TITLE = "title";
    public static final String SUBTITLE = "subtitle";
    // This is the SQL Statement that will be executed to create the table and columns
    // "_id" is recommended to be a standard first column and primary key
    private static final String SQL_CREATE = "CREATE TABLE " + MYTABLE + " ( " + ID + " INTEGER PRIMARY KEY, " + TITLE + " TEXT, " + SUBTITLE + " TEXT) ";
    public MyDbHelper(Context context) {
      // the third parameter is SQLiteDatabase.CursorFactory: to use for creating cursor objects, or null for the default This value may be null.
      super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }
    @Override
    public void onCreate(SQLiteDatabase db) {
      db.execSQL(SQL_CREATE);
    }
      @Override
    public void onOpen(SQLiteDatabase db) {
      // invoked when getWriteableDatabase() is called for the first time
    }
    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
      // This is only called if the DATABASE_VERSION changes
      // Possible actions - delete table (ie DROP TABLE IF EXISTS mytable), then call onCreate
    }
  }
  ```
- In main activity class, create a global instance of our SQL Helper class, `MyDbHelper mydbhelp = new MyDbHelper(this);`, then get an instance of the database using the helper `SQLiteDatabase db = mydbhelp.getWritableDatabase();` before starting accessing the database(e.g. inside a button handler function)
  - call `mydbhelp.close()` when done, usually in `onDestroy()`
- The database is not actually created or opened until one of `getWritableDatabase()` or `getReadableDatabase()` is called
- The `db` object of the `classSQLiteDatabase` instance can do
  - `long newrowID = db.insert("mytable",null, values);`
    - values is a `ContentValues` class object, each one represents a record with multiple columndata
    ```java
    ContentValues values = new ContentValues();
    values.put("title", title.getText().toString());
    values.put("subtitle", subtitle.getText().toString());
    ```
    - the second parameter expects a list of the column names for insert, when `null` all column will be changed in the update
  - `int i = db.update(mydbhelp.TABLE_NAME,contentValues, mydbhelp._ID + " = " + _id, null);`
  - `db.delete(mydbhelp.TABLE_NAME, mydbhelp._ID + "=" + _id, null);}`
- Cursor - represents the entire result set of the query
  - Once the query is fetched a call to `cursor.moveToFirst()` is made, calling moveToFirst() does two things:
    - It allows us to test whether the query returned an empty set (by testing the return value)
    - It moves the cursor to the first result (when the set is not empty)
  ```java
  public Cursor fetch() {
    String[] columns = new String[] { mydbhelp._ID, mydbhelp.SUBJECT, mydbhelp.DESC};
    Cursor cursor = db.query(mydbhelp.TABLE_NAME, columns, null, null, null, null, null);
    if (cursor != null) {
      cursor.moveToFirst();
      }
      return cursor;
    }
  ```
  - Read cursor in main activity
  ```java
  public class ListActivity extends AppCompatActivity {
    // Create a global instance of our SQL Helper class
    MyDbHelper mydbhelp = new MyDbHelper(this);
    /**
      * onCreate - get an instance of our database, use a cursor to display the values
      * @param savedInstanceState (default)
      */
      @Override
      protected void onCreate(Bundle savedInstanceState) {
      super.onCreate(savedInstanceState);
      setContentView(R.layout.activity_list);
      // Get an instance of the database using our helper
      SQLiteDatabase db = mydbhelp.getReadableDatabase();
      // A projection defines what fields we want to retrieve.
      String[] projection = { "_id", "title", "subtitle"};
      // db.query will retreive the data and return a Cursor to access itCursor
      Cursor mycursor = db.query("mytable", projection, null,null, null, null, null);
      String results = "";
      // Loop through our returned results from the
      while(mycursor.moveToNext()) {
        String title = mycursor.getString( mycursor.getColumnIndex("title") );
        String subtitle = mycursor.getString( mycursor.getColumnIndex("subtitle") );
        long itemID = mycursor.getLong( mycursor.getColumnIndex("_id") );
        // We could add our results to an array, or process them here if we want
        results += itemID + " " + title + " " + subtitle + "\n";
        }
        // Close the cursor when we're done
        mycursor.close();
        // Show our
        TextView output = (TextView) findViewById(R.id.outputtext);
        output.setText(results); // XXX TODO fix this
      }
    }
  ```
  - For `db.query()`, `mycursor = db.query("mytable", columns, whereClause, whereArgs, groupBy, having, orderBy);`
    - for where clause include `?` for things that are dynamic
    - `whereArgs` assign values in `?` used in the `whereClause` in the order they appear
    - For example:
    ```java
    String[] tableColumns = new String[] {"column1","(SELECT max(column1) FROM table2) AS max"};
    String whereClause = "column1 = ? OR column1 = ?";
    String[] whereArgs = new String[] {"value1","value2"};
    String orderBy = "column1";
    Cursor c = sqLiteDatabase.query("table1", tableColumns, whereClause, whereArgs, null, null, orderBy);
    int idx = c.getColumnIndex("max");
    ```
  - Use SimpleCursorAdapter for ListView
    ```java
    SQLiteDatabase db = mydbhelp.getReadableDatabase();
    String[] columns = {MySQLHelper.ID, MySQLHelper.PRODUCT, MySQLHelper.SERIAL};
    Cursor mycursor = db.query(MySQLHelper.MYTABLE, columns, null, null, null, null, null);
    SimpleCursorAdapter adapter = new SimpleCursorAdapter(this, android.R.layout.two_line_list_item, mycursor, new String[]{MySQLHelper.PRODUCT, MySQLHelper.SERIAL}, new int[]{android.R.id.text1, android.R.id.text2});
    ListView productList = findViewById(R.id.product_list);
    productList.setAdapter(adapter);
    productList.setOnItemClickListener(this::onItemClick);
    mycursor.close();
    ```
    - The integer array in the SimpleCursorAdapter constructor corresponding to the textview widget id in the chosen layout from the second parameter

##### Cursor

#### Useful Libraries

##### GSON

- Gson (also known as Google Gson) is an open-source Java library to serialize and deserialize Java objects to (and from) JSON
- add `implementation 'com.google.code.gson:gson:2.8.6'` explicitly to `gradle.build` file at the application level in the dependencies section before use
- Right click the folder that contains the java files you are working with and create new java class files each with the following classes
- To use GSON declare a data model

  ```java
  public class MyObject {
    public String   _id;
    public String   Year;
    public String   Num;
    public String   Title;
    @Override
    public String toString() {
      return Year + " " + Num + " " + Title;
    }
  }
  ```

- Declare a data model list

  ```java
  public class MyObjectList extends ArrayList<MyObject> {
    private static final long serialVersionUID = 1L;
  }
  ```

- Convert object to json string

  ```java
  Gson gson = new Gson();
  String jsonStr = gson.toJson(myObject);
  ```

- Get object instance from json string

  ```java
  Gson gson = new Gson();
  MyObject obj = gson.fromJson(jsonStr, MyObject.class);
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
- Permissions are added here and users will be asked to grant these permission when the app is first launched, they should be added at the top inside `<manifest></manifest>`
  - Normal permissions: allow access to data and actions that extend beyond your app's sandbox. However, the data and actions present very little risk to the user's privacy, and the operation of other apps. It doesn't require any special dialogs to ask for permission
    - `<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />`
    - `<uses-permission android:name="android.permission.INTERNET" />`
  - Runtime permissions: also known as dangerous permissions, give your app additional access to restricted data, and they allow your app to perform restricted actions that more substantially affect the system and other apps. Therefore, you need to request runtime permissions in your app before you can access the restricted data or perform restricted actions.
    - `<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />`
    - `<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />`
    - `<uses-permission android:name="android.permission.RECEIVE_SMS" />` permission to read new SMS messages
  - Special permissions: Special permissions correspond to particular app operations. Only the platform and OEMs can define special permissions. Additionally, the platform and OEMs usually define special permissions when they want to protect access to particularlypowerful actions, such as drawing over other apps.
    - `<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />` Screen Overlay Permission, allows the app draw over another one without the screen overlay warning

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
- declaration for the broadcast receiver, this example will invoke the `MyReceiver` class in the app, whenever a message is received
  ```xml
  <receiver
    android:name=".MyReceiver"
    android:enabled="true"
    android:exported="true">
    <intent-filter>
      <action android:name="android.provider.Telephony.SMS_RECEIVED" />
    </intent-filter>
  </receiver>
  ```
  - This info is registered through the Android OS, it will be executed even the app is not running
  - In Android 7.0 (API level 24) picture and video broadcasts were removed to improve general performance
  - In Android 8.0you cannot use the manifest to declare a receiver for most implicit broadcasts (broadcasts that don't target your app specifically).

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
- All the definition are about the single element it belongs to
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
- Namespaces
  - `xmlns` it defines base namespace Uniform Resource Indicator(URI) path for other namespaces
  - `app` namespace that can access to `parent` element
  - `android` namespace includes all other attributes in the attribute panel
  - `tools` namespace for some design-time features

##### Layout Types

- `<LinearLayout>`
  - It defines layout container that can grow in two direction, either vertical or horizontal
  - `android:orientation` can be either `"vertical"` or `"horizontal"`
  - `android:layout_weight` controls how much space its component takes
    - set `android:layout_height`(when vertical) or `android:layout_width`(when horizontal) to `0dp` and `android:layout_weight` to `1` can make all component evenly distributes with zero space in between
- `<RelativeLayout>` (legacy)
  - It defines elements relative to sibling elements (such as to the left-of or below another view) or parents (such as aligned to the bottom, left or center)
  - `android:layout_centerHorizontal="true"`, `android:layout_centerVertical="true"`, `android:layout_centerInParent="true"` for centering elements
- `<ConstraintLayout>`
  - It defines elements relative to others
  - Move a vertically or horizontally centered element will introduce bias
- `<FrameLayout>` it is designed to block out an area on the screen
  - Attribute `layout_gravity` can quickly align content relative to its parent, to `start`(left), `center`, or `end`(right)
- Layouts have a `tools:context` attribute which is used to specify the assicoate class name for the editor

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
  - Use theme `Theme.MaterialComponents.DayNight.DarkActionBar.Bridge` to change the button background color
- Other than `DarkActionBar`, it can be `NoActionBar`. As a result the app title will be removed

##### `strings.xml`

- It stores all the hardcoded strings
- The file has parent element `<resources></resources>`
- It consisted of multiple string records as `<string name="key">value</string>`
  - It can hold formatted string with variable specified in java code, `<string name="hello">Fragment %1$s The Switch is %2$s</string>`
  - use `getResource(R.string.string_name, arg1, arg2).getString()` method to get formatted string with value
- It can stores arrays as `<string-array name="key"><item>A</item><item>B</item><item>C</item></string-array>`
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
  - It needs to be unique
  - When use attribute panel to change element keys using refactor, all existing key value in the project will be replaced, use `.xml` editor if only want to change the key for selected object
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
