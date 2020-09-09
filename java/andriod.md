# Andriod Development with Java

## Introduction

- Andriod Studio is the IDE for Andriod App Development
- Andriod SDK is provided by various versions of SKD platforms. Each marjor platform version has a name. E.g. `Andriod 10.9` is called `Q`.
- Each SDK platform version is associated with an API level, API level is used to determined the apps compatibility.

## Setup

### Installation

- [Download](https://www.oracle.com/ca-en/java/technologies/javase-downloads.html) and install the lastest Java SE Development Kit.
  - For Mac using Brew, run `brew cask install java` and run `brew cask info java` to verify.
- [Download](https://developer.android.com/studio) and install Android Studio.
  - For Mac, run `brew cask install android-studio`.
- Install the preferred SDK platform for the devices to use when testing in SDK Manager.

### Open a Project

- Create a new project
  - Select `start a new project`.
  - Select the `Empty Activity` template(recommanded)
  - The package name is the unique identifier of the app. Usually it is the organization or personal domain name in reverse order.
  - The minimum API level controls the minimum SDK platform version that the app will support.
- Open an existing project
  - In the welcome page, select and open the existing project folder
  - Open the existing project's gradle file with Andriod Studio.
  - Open the from the menu bar.

### Configuration

In the preference menu:

- Change color and font size
- Enable auto import
- And prefix for Java name convention

Setup version control

### Run Apps

#### Emulator

- Install the required images in the SDK manager
  - If the host machine has an Intel CPU, install the `Intel X86` images.
    - Install the `Intel X86 Emulator Accelerator` for a faster performance
  - If the host machine has an Intel CPU, install the `ARM` images for some older versions of the SDK platforms.
- Open Andriod Virtual Device(AVD) Manager and configure and create a new virtual device with preferred image files.

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

## Project Structure

### `manifests` folder

#### `AndroidManifest.xml`

- It contains the general information about the project
  - path to icons and round icons folders
  - the launch activity

### `res` folder

- It contains all the app resources.
- Right click `res` folder and open the `Image Asset`, this tool can be used to generate icons for the app.
- The image files spec can be found [here](https://developer.android.com/training/multiscreen/screendensities).
- Images can be resize and organize by the [Java Final Resizer](https://github.com/asystat/Final-Android-Resizer).
  - When images have been resized, copy and paste the output image directly to the `res` folder.

#### `drawable` folder

- It stores all images for the app

#### `minmap` folder

- It stores the app icon file

- It can has two folder one contains square app icons, the other one contains round app icons.

## Android Studio IDE
