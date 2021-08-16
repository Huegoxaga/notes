# Raspberry Pi

## Introduction

- It is a series of development board developed by the Raspberry Pi Foundation in the UK.
- It can install an entire OS as a fully functional computer.

## OS

- Linux distribution Raspberry Pi OS (previously called Raspbian) is the official OS for Raspberry Pi.
  - It is based on Debian Buster
  - The `with recommended software` version comes pre-installed with plenty of software for education, programming and general use. It has Python, Scratch, Sonic Pi, Java and more.
  - the `with Desktop` version provides a desktop GUI.
  - the `lite` version contains the minimal image
  - Don't be confused with `Debian with Raspberry Pi Desktop`, It is an OS for PC or Mac, not Raspberry Pi.
- New Out Of Box Software (`NOOBS`) is an easy operating system installation manager for the Raspberry Pi.
- It can even install Windows 10 IoT Core which allows it to run on Windows
- It can run Andriod OS using Android Things platform.
- After downloading the image the unzip error is caused by the uncompatibility of the WinRAR of Windows. Use `7-Zip` instead

## Models

- Currently Raspberry Pi has generation from 1 to 4.
- Based the connection features Raspberry Pi has Model A, A+, B, B+, Zero, and Zero W(Wireless).
  - Generally compare models in the same generation, for the price from low to high, `A` -> `A+` -> `B` -> `B+`. The perform is better, models are improved in USB, pin number and `A` model can not establish wireless connection.
  - Raspberry Pi Model B was the first model which is realsed in February 2012.
  - The Zero model is the smallest board.
- There are also Raspberry Pi Compute Module for industrial application
- All current models uses micro SD card.
  - Most OS requires 8GB SD card. Windows 10 IoT Core requires class 10 card.
  - [Click here](https://elinux.org/RPi_SD_cards) to verify the SD card compatibility
- Raspberry Pi uses 5V DC power supply, but the current capacity varies based on model types. [Click](https://www.raspberrypi.org/documentation/hardware/raspberrypi/power/README.md) to see the required power supply
  - A stable power supply will help the board and SD card healthy
- Raspberry Pi Zero
  - It has camera connector for 1.3 version only. with a 0.5mm cable.
  - It has holes for TV pins, allows RCA jack connection for video output.
  - It has holes for RUN pins, allows the installation for reset button.
  - It uses mini HDMI port

### Pins

- It does not have analog pins, an external digital to analog converted is required.
- Precaution
  - It has limited fueses, so power off when connecting pins.
  - only 3.3V on GPIO pins.
  - Current coming out of the output pin should be less than 3mA
  - Current coming out of the 3.3V supply pin should be less than 50mA
  - Current coming out of the 5V supply pin should be less than 250mA
  - never short curcuit the pins with metal.
  - 330 ohm resistor is suggested to limit the current.
- There is a pin number for all pins, these number can be used in Board Mode.
- Pins can be categorized as:
  - Power supply pins, there are supply pins for 3.3V and 5V
    - GPIO works at 3.3V for all inputs and outputs.
  - GPIO pins, there are general purpose GPIO pins and some of the GPIO pins can also serve a certain task.
    - GPIO pins themselves are also numbered. These number can be used in BCM mode.
  - Ground pins - used with the supply pins for ground.
- All pins have both pull-up and pull-down resistors.

## Setup

- Etcher is a great tool to flash SD cards.
  - [Click here](https://www.balena.io/etcher/) to download
  - Optionally, use the official tool [Raspberry Pi Imager](https://www.raspberrypi.org/downloads/) to download and flash SD card with one click.
- [Clich here](https://www.raspberrypi.org/downloads/raspberry-pi-os/) to download the OS that will be flashed to the SD card.
- Install etcher and download the OS image in a `zip` file then use the Etcher software to flash the OS onto the SD card.
- Plug in the SD card, connect Raspberry Pi to a screen and input devices, then boot up the device.
- Backup
  - For Window machine, use the [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/) and read from the SD card to an image file.
  - For Mac, use Disk Utility, and the Image option in the menu bar.

## Raspberry Pi OS

- The system configuration page will pop-up after first boot up, follow the steps to configure language, WiFi, and reset the password.
  - The settings are always available in system config GUI or CLI.
  - The initial username is `pi`, password is `raspberry`
- Enable the peripherals of the board in the interfaces page of the Raspberry Pi Configuration menu.
  - Raspberry Pi Camera can be enabled here
- When the board has no input and output devices connected, it is in a headless mode. Follow the step to configure the board in headless mode.
  - After flash the SD card, add the `wpa_supplicant.conf` file for WiFi setup to the SD card root folder with the following content.
    ```
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    country=<TWOLETTERCOUNTRYCODE>
    network={
      ssid="SSID"
      psk="PassWord"
      key_mgmt=WPA-PSK
      priority=1
    }
    network={
      ssid="MY_SSID2"
      psk="MY_PASSWORD2"
      key_mgmt=WPA-PSK
      priority=2
    }
    ```
    - [Click](https://www.nationsonline.org/oneworld/country_code_list.htm) to find the country code.
    - The SSID needs to be broadcast for connection
  - Create an empty file with name `ssh`.
  - Insert the SD card and boot up Raspberry Pi, then SSH to board.
    - try `ping raspberrypi` to get the board IP.
- VNC Server can allows to view the GUI interface of the OS from any client
  - Enable the VNC Server in `sudo raspi-config`.
  - [Click](https://www.realvnc.com/en/connect/download/viewer/) to download the VNC on remote machine, then connect to the board by entering the PI's IP in the search bar to view its GUI.
    - Login to a VNC account for both VNC server and VNC viwer allows remote connection through cloud without using shared WiFi.
- It has a `Thonny Python IDE` which can run and debug python progarm that interact with peripherals using peripherals's own python libraries(Ex, `GPIO` and `PiCamera`).
- Turning the board into an Alexa device
  1. register a product in Alexa Voice Service(AVS) console
  2. Update packages list `sudo apt-get update`
  3. Install the latest pacakages and update the OS, `sudo apt-get dist-upgrade`
  4. Install git, `sudo apt-get install git`
  5. Install specific version of CherryPy due to AlexaPi bug `sudo pip install CherryPy==17.4.0`
  6. Navigate to the opt folder `cd /opt`
  7. Clone the Alexa Pi git repository `sudo git clone https://github.com/alexa-pi/AlexaPi.git`
  8. Run the Alexa Pi installation script `sudo ./AlexaPi/src/scripts/setup.sh`
  9. Enter product info obtained from product registration
  10. From the CLI prompt, perform the step to give appropriate permissions from your Amazon Dev Account for the Alexa Voice Service
  11. Starting the Alexa Pi Service `sudo systemctl start AlexaPi.service`
  12. Stopping the Alexa Pi Service `sudo systemctl stop AlexaPi.service`
- Run scripts after reboot, run `crontab -e` open cron table
  - `@reboot python /home/pi/Desktop/Run/*.py &` run all python files in the Run folder in the Desktop.

### Raspberry Pi OS Lite

- VNC server
  - Need to run `apt-get install tightvncserver` to install the server
  - run `sudo tightvncserver -geometry WidthxHeight` then set password and start the server
    - using sudo will open a root connection, in this mode browser can't be open.
    - use `tightvncserver -geometry WidthxHeight` command to connect as a normal user.

### CLI

- run `sudo raspi-config` will open a GUI in the terminal to make board configuration.
- run `omxplayer <VideoPath>` to play videos using the pre-installed video player.

### Libraries for Raspberry Pi

- GPIO can be controlled in various language

#### Python Library

- Example I/O
  ```py
  import RPi.GPIO as GPIO #Use GPIO library
  import time #Use time library
  GPIO.setwarnings(False)
  ledPin = 11    # pin11 is connected to the led anode (+ve pin), cathode(-ve pin) connected to pin9 GND
  buttonPin = 16  # pin 16 is connected to the button - other button pin is connected to gnd - pin 14
  GPIO.setmode(GPIO.BOARD)  # Numbers GPIOs by physical location
  GPIO.setup(ledPin, GPIO.OUT)    #set ledPin's mode as output
  GPIO.output(ledPin, GPIO.LOW)   #initially turn off the led
  GPIO.setup(buttonPin, GPIO.IN, pull_up_down=GPIO.PUD_UP)    #Set buttonPin as input and enable pullup resistor
  while True: #Loop indefinitely
  GPIO.wait_for_edge(buttonPin, GPIO.FALLING) #Button was pressed, only defect changes
  #input_state = GPIO.input(buttonPin) #Retrieve the current state of the button pin
  print('Button Pressed') #Display button pressed
  GPIO.output(ledPin, GPIO.HIGH)  # Turn led on
  GPIO.wait_for_edge(buttonPin, GPIO.RISING) #Button was released
  GPIO.output(ledPin, GPIO.LOW)  # Turn led off
  GPIO.cleanup(); #Clean up when exiting the program
  ```
- Camera Example
  ```py
  from picamera import PiCamera
  from time import sleep
  camera = PiCamera()
  try:
      # preview(not required for taking photos)
      camera.start_preview() #preview can't be seen from the VNC, HDMI output is required.
      sleep(10)
      camera.stop_preview()
      pass
  finally:
      camera.close()
  # take pictures
  for i in range(5):
      sleep(5)
      camera.capture('/home/pi/Downloads/photos/image%s.jpg' % i)
  # record video
  camera.start_recording('/home/pi/Downloads/photos/video.h264')
  sleep(10)
  camera.stop_recording()
  # preference
  camera.brightness = 70
  camera.annotate_text = "hi"
  camera.resolution = (2592, 1944)
  camera.framerate = 15
  # effects
  camera.start_preview()
  for effect in camera.IMAGE_EFFECTS:
      camera.image_effect = effect
      camera.annotate_text = "Effect: %s" % effect
      sleep(5)
  camera.stop_preview()
  ```
- Working with events
  ```py
  import RPi.GPIO as GPIO #Use GPIO library
  import time #Use time library
  pirPin = 7  # pin 7 is connected to output from the PIR motion sensor, 5V to pin 2, GND to pin 6
  buzzerPin = 11  # pin 11 is connected to the +ve buzzer pin; -ve connected to pin 9 GND
  GPIO.setmode(GPIO.BOARD)  # Numbers GPIOs by physical location, when USB ports at bottom, pin 1 is at top left, pin 2 is at top right, pin 3 is at second row at left, etc.
  GPIO.setmode(GPIO.BCM)  # Numbers GPIOs by BCM, e.g. 4 for GPIO4 pin
  GPIO.setup(pirPin, GPIO.IN); #set the pirPin as input
  GPIO.setup(buzzerPin, GPIO.OUT); #set the buzzer pin as output
  GPIO.output(buzzerPin, GPIO.LOW) #initially turn off the buzzer
  GPIO.setup(pirPin, GPIO.IN, pull_up_down=GPIO.PUD_DOWN); #set the pirPin as input with pull up resistor
  GPIO.setup(pirPin, GPIO.IN, pull_up_down=GPIO.PUD_UP); #set the pirPin as input with pull down resistor
  #define alarm events
  def soundAlarm(pirPin):
    #sound alarm (for 2 seconds )
    print("Sound Alarm")
    GPIO.output(buzzerPin, GPIO.HIGH)  # Turn buzzer on
    time.sleep(2) # Pause for 2 seconds
    turnOffAlarm()  # Turn buzzer off
  def turnOffAlarm():
    #turn off alarm
    GPIO.output(buzzerPin, GPIO.LOW)  # Turn buzzer off
    #adding a callback function when the pir sensor output rises when motion is detected
    GPIO.add_event_detect(pirPin, GPIO.RISING, callback=soundAlarm);
    #try catch block to perform GPIO cleanup
  try:
    while True:
        pass
  except KeyboardInterrupt:
    print("Ctrl+C Pressed")
  finally:
    #clean up the GPIO pins
    GPIO.cleanup()
  ```
