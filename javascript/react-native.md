# React Native

* It can be used to develop mobile app that run on both Android and iOS platforms.
* [Click here](https://facebook.github.io/react-native/docs/getting-started) to see React Native documents.

## Using Expo

It is easy to start with, but has some limitation.

### Installation

1. download node.js
2. run: `sudo npm install expo-cli —global`.

### Create Project

1. Navigate to the project folder cd /project-folder
2. run: `expo init project-name`
3. select template
4. enter the name for app
5. `cd` to the project folder
6. run: `npm start`
7. leave the terminal open while developing. hold control+C to cancel or type npm start to restart.

### Connect

1. download expo client app on mobile device.
2. scan the QR code for the project or type the IP address of the project page in the mobile browser and open the link with expo app.
3. click Got It

### Install Emulators

* For Android:
  1. Install Android Studio
  2. Install require packages
  3. Setup the bash environment.
  4. Launch an emulator using AVD manager
  5. In expo terminal select command to launch app in Android Emulator.
* For iOS
  * Install Xcode
  * Install Xcode CLI
  * Launch Virtual Devices from Emulator.
  * In expo terminal select command to launch app in iOS Emulator.

### Publishing

The packager will minify all your code and generate two versions of your code \(one for iOS, one for Android\) and then upload those to a CDN.

1. optimized the assets run: `expo optimize`.
2. run: `expo publish`.
3. Start the build, Run: `expo build:android` or `expo build:ios`

### Transfer the Project to React Native cli

Expo has many limitations, in order to transfer the project to react native cli to gain complete control.

1. run: `expo eject`
2. choose the "Bare" option.
3. You will prompted with several questions and then the native iOS and Android projects will be created.
4. Delete the newly create folders if deciding to keep using expo.
5. follow react native cli instruction to run the existing project.

## Using react native cli on Mac for iOS

1. install Xcode
2. install Xcode CLI Tools in preference/Location select the cli version.
3. Install Emulator in Preference/Components
4. install CocoaPods run: `sudo gem install cocoapods` in project root folder
5. Create new project run: `npx react-native init projectName`.
6. To start the created project or existing project, cd to iOS folder run: `pod install`
7. cd to the project folder
   * run: `npx react-native run-ios` \(to start iOS Emulator\)
   * or, `react-native run-ios --simulator="iPhone 5s"` to run on certain device.
   * run: `xcrun simctl list devices` to check available devices.
8. To run the project on a real device, run the `.xcodeproj` file or `.xcworkspace` using Xcode to register and run the project using real devices.

### Running iOS Projects Repo for the First Time

1. run `npm install`
2. run `cd ios && pod install`
3. Open the project in Xcode, Sign in the Developer Account.
4. Run in Xcode or run `npx react-native run-ios`.

### Publish iOS Project

1. re-enable ATS prior to building your app for production by removing the localhost entry from the NSExceptionDomains dictionary and setting NSAllowsArbitraryLoads to false in your Info.plist file in the ios/ folder.
2. Configure your app to be built using the Release scheme, go to Product → Scheme → Edit Scheme. Select the Run tab in the sidebar, then set the Build Configuration dropdown to Release.
   * It will also bundle the JavaScript locally, so you can put the app on a device and test whilst not connected to the computer.
3. You can now build your app for release by tapping ⌘B or selecting Product → Build from the menu bar.
4. Distribute the app to beta testers and submit the app to the App Store.

## Using react native cli on Mac for Android

1. install java sdk
2. install android studio
3. install android sdk
4. run additional environment setup, add following path:

```bash
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

1. run: `npx react-native run-android`

## Files

* `.expo` folder, it is used for expo config, only exist when using expo
* `asset` folder, images
* `node_modules`, auto managed modules folder.
* `app.json`, configuration for the app
* `babel.config.js`, babel configuration file.
* `package.json`, manage modules for the project.
* `App.js`, the App Component File.

  ```javascript
  import React from "react"; //import react, for jsx
  import { StyleSheet, Text, View } from "react-native"; //import for react native components.

  export default function App() {
    return (
      <View style={styles.container}>
        {" "}
        //view component with styles
        <Text>Open up App.js to start working on your app!</Text> // react
        native text component
      </View>
    );
  }
  // set the style, styles use css syntax, but it is done via js.
  const styles = StyleSheet.create({
    container: {
      flex: 1,
      backgroundColor: "#fff",
      alignItems: "center",
      justifyContent: "center"
    }
  });
  ```

## Core Component

* See a full list of core component at [here](https://facebook.github.io/react-native/docs/components-and-apis.html)

### View

* container for component in the screen.
* use flex box to organize children components.

### ScrollView

* a view component that is scrollable.

### Touchable

* make components inside the component touchable.

### touchableOpacity

* make components touch and respond to the user an opacity effect when touched.

### TouchableHighlight

* touchable and change background color when touched.

#### properties

* `activeOpacity = {0.5}` set the opacity level for the effect.

### FlatList

* It is useful for a long list

#### properties:

* `data` an array of object for the list, the object must have a key or id property.
* `renderItem` a function a process the data and return components for each element of the array object.
* `keyExtractor` a function a take object element and index and return the actually object property as key.

### SafeAreaView

* view inside safe area.

### Text

* contain text string.

### Image

* contain image
* Property `source={ {uri:"https://link.com"} }/>`

### Button

* a button

#### properties:

* title: the title of the button.

### TextInput

* allows user input text.

#### properties:

* placeholder
* borderColor
* borderWidth

### Modal

* wrap component, in a movable component.

#### properties

* visible true or false
* animationType

## Styling

### inline style

attach the style sheet as an view property.

```javascript
<View style={styleName: value}>
```

### stylesheet object

1. import the StyleSheet

```javascript
import StyleSheet from "reach-native";
```

1. wrap all styles in an object.

```javascript
const styles = StyleSheet.create({
  settingName1: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center"
  },
  settingName2: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center"
  }
});
```

1. then attach the object to a component

```javascript
<View style={styles.settingName1}>
```

## Customized Components

* just as App.js wirite the proper functional component and export.
* pass data use props
* it can the be used in app.js after proper import of this customized component.

## Debug

* access debug control panel:
  * In emulator press command + d for iOS emulator, press command + m for Android emulator.
  * on real device: Shake the device to open the Developer menu,
  * debug control panel has the following options.
    * Debug Remotely: enable debug with chrome inspector. can set break point by clicking the link number of the source codes.
    * Performance monitoring: see the hardware performance
    * toggle inspector: check the status of components in the app.
* Optionally download the react native debugger and run it after debug remotely is on.
* Always remember to stop the debug remotely mode after it is done.

## Modules

* the following modules can be added in the project's node\_modules folder.
* Modules are written in Javascript and managed and installed by npm.
* Modules add functionality to the app. Install a module by running `npm install react-native-module-name` after `cd` to the project folder.
* Linking make sure the app uses the package not the default ones, no need after React Native 0.60 or the module doesn't support auto-linking.

  ```text
  react-native link react-native-moduleName
  ```

* for iOS, run: `pod install` in the ios folder after add installing the module.
* restart everything after installing modules
* look at yellow prompts for error when using npm install. install all the required packages.
* add path in the podfile if pod install can't find the modules.

### Location Service

* [Click](https://github.com/Agontuk/react-native-geolocation-service) to see its documents
* using react-native-geolocation-service for higher accuracy and response time for android devices.

#### for iOS

* You need to include the NSLocationWhenInUseUsageDescription key in Info.plist to enable geolocation when using the app. In order to enable geolocation in the background, you need to include the NSLocationAlwaysUsageDescription key in Info.plist and add location as a background mode in the 'Capabilities' tab in Xcode.
* this library assumes that location permission is already granted by the user, so you have to use PermissionsAndroid to request for permission before making the location request.

#### Installation

1. In the project folder run: `npm install react-native-geolocation-service`
2. update pod file, add the following line in pod file.

```text
pod 'react-native-geolocation', path: '../node_modules/@react-native-community/geolocation'
```

1. run, `pod install` in ios folder.

```javascript
...
import Geolocation from 'react-native-geolocation-service';
...

componentDidMount() {
    // Instead of navigator.geolocation, just use Geolocation.
    if (hasLocationPermission) {
        Geolocation.getCurrentPosition(
            (position) => {
                console.log(position);
            },
            (error) => {
                // See error code charts below.
                console.log(error.code, error.message);
            },
            { enableHighAccuracy: true, timeout: 15000, maximumAge: 10000 }
        );
    }
}
```

Methods [Click](https://github.com/Agontuk/react-native-geolocation-service#api) to see more Methods

### Voice Recognition

#### Installation

In the project folder run: `npm install react-native-voice`

#### permission for iOS

add permission in the plist file after bundle version

```text
<key>NSMicrophoneUsageDescription</key>
<string>Description of why you require the use of the microphone</string>
<key>NSSpeechRecognitionUsageDescription</key>
<string>Description of why you require the use of the speech recognition</string>
```

### Sound

#### Installation

In the project folder run: `npm install react-native-sound --save`

#### Example

```javascript
import Sound from "react-native-sound";

Sound.setCategory("Ambient", true);
const buttonPress = new Sound(require("../audio/button.mp3"), error =>
  console.log(error)
);
export const playButtonPress = () => {
  buttonPress.play(success => buttonPress.reset());
};
//call events
<TouchableOpacity onPress={playButtonPress}>
  <Text>Click me</Text>
</TouchableOpacity>;
```

### Maps

* For `react-native-maps`, initialRegion must be set if immediately followed by animateRegion during during launch.

### File System

* This module provide access to the folders inside the app folder in the mobile OS file system.
* Folders will be accessed using the following constant value.
  * `MainBundlePath` \(String\) The absolute path to the main bundle directory \(not available on Android\)
  * `CachesDirectoryPath` \(String\) The absolute path to the caches directory
  * `ExternalCachesDirectoryPath` \(String\) The absolute path to the external caches directory \(android only\)
  * `DocumentDirectoryPath` \(String\) The absolute path to the document directory
  * `TemporaryDirectoryPath` \(String\) The absolute path to the temporary directory \(falls back to Caching-Directory on Android\)
  * `LibraryDirectoryPath` \(String\) The absolute path to the NSLibraryDirectory \(iOS only\)
  * `ExternalDirectoryPath` \(String\) The absolute path to the external files, shared directory \(android only\)
  * `ExternalStorageDirectoryPath` \(String\) The absolute path to the external storage, shared directory \(android only\)
* Follow the [steps](https://github.com/itinance/react-native-fs) to setup and use the module.
* [Click here](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html) to learn more about iOS file system.

## Deploy

### Deploy iOS App

1. Add the script given below to the `package.json` file in the React Native project.

```javascript
"scripts": {
"build:ios": "node node_modules/react-native/local-cli/cli.js bundle --entry-file='index.js' --bundle-output='./main.jsbundle' --dev=false --platform='ios' --assets-dest='./ios'"
}
```

1. Run `npm run build:ios` command in the project folder.
2. add `main.jsbundle` and `assets` foler to the project folder in Xcode.
3. Set Release Scheme in Xcode and run.

