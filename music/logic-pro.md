# Logic Pro

## Introduction

- Logic Pro is a digital audio workstation (DAW) and MIDI sequencer software application for the macOS platform

## Setup

- Relocate Sound Libraries to desired storage location(internal or external) by clicking `Logic Pro` -> `Sound Library` -> `Relocate Sound Library..` on the top menu, Select the `Sound Library Manager..` to download desired library or `Download All Available Sounds`
  - `Reinstall Sound Library` will clear and reinstall all existing libraries
- From the top menu, `Preferences` -> `Audio` -> `Devices` tabs specify the audio input and output devices
  - Audio Interface is required for audio input from electric instruments or vocal sounds from microphones
  - Using the built-in speakers together with the built-in microphone can cause feedback, Connect headphones or choose a different audio device to avoid it
- From the top menu, `Preferences` -> `Advanced Tools...`, enable all advanced tools

## Create a New Project

- Press `Shift` + `Command` + `N` to create a new empty project

### Create from Template

- Press `Command` + `N` to create a new project from template

## Create a Track

- A track need to be created once a project is created
- Options
  - Select number of tracks for this type
  - Select input/output channel
  - Select input/output devices
- Track Types
  - Software Instrument - sound from libraries based on software MIDI input
  - Audio - sound sampled from input device
  - External MIDI - sound from libraries based on external MIDI device input
  - Drummer - built-in drummer software
  - Guitar or Bass - sound from guitar processed by built-in amplifier libraries
- When the project is opened, a track can be created by clicking the plus button(`Option + Command + N`) above the track headers
- Tracks can be duplicated by selecting and clicking on the duplicate button above the track headers
- Double clicking on the empty space below track header to duplicate a selected track
- Clicking on the Global Track icon above track headers to add `Arrangement` info, `Maker` notes, Time `Signature`, `Tempo` as a global track on top of all tracks
- Press `O` to open the Apple Loop Browser, to filter on the top and click to preview loops, then drag the loop to an empty track area to create loop track
  - Loops with green icons are MIDI loops
  - Loops with blue icons are audio loops
  - Loops with yellow icons are drum loops

## Project Setup

- The project interface will be shown after the first track is created
- `LCD` display in the centre of the top control bar can be used to setup project tempo and time signature
  - Open the drop-down and select `Custom` to display more info
- Adjust the master volumn on the top control bar

## Save a Project

- A project can be saved as a single package or a project folder
- Only Audio Files are required to be copied
  - All project related files need to be copied when the project will be moved to another computer

## Work with Tracks

- The Inspector panel is used to change track property
- It is located on the left side, press `I` to open and close
  - Press `Help` icon on top-left corner will display quick help at the top of the inspector panel when hovering the mouse over buttons and panels
- In the region panel, following effects can be added between all regions
  - cross fade

### Track Header

- Clicking on the `M`(Mute) icon or press `M` key to mute
  - `Control + M` will mute one clip
- Clicking `S`(Solo) icon, or Press `S` key to mute all other tracks
  - `Control + S` will solo one clip
- Clicking on the `R`(Record Enable) icon to enable the recording for this track
- Clicking on the `I`(Input Monioring) icon to output the input audio to the monitor speaker
- Volumn control controls the input channel volumn of this track
- Pan control controls balance of the left and right input volumn of this track
- Double clicking the track name to rename the
- Right click to change track icon

### Channel Strip

- The channel strip panel is located at the bottom of the Inspector pannel
- The channels of each track can be setup separately
- The left part of the channel strip panel controls the input, the right part controls the output

#### Channel Strip Settings

- A preset settings have a set of plug-in activated each with a predefined configration
- Press `Y` to close and open the Library panel, select to change channel strip setting
  - or change setting by selecting `setting` in the channel strip panel
- Many preset settings for guitar and bass are moved to the `Legency` category if using audio track type to record guiter and bass
- Preset setting uses plug-ins to add a post-effect to the recording, it can be changed anytime after the recording

#### Channel Strip Plug-in

- They can be turn off by clicking the power button or select `No Plug-in` in the drop-down
- Tuner - helps tune the input instrument for audio tracks, or select the `fork` icon on the top control panel
- MIDI FX - helps create MIDI effect using one of the following plug-in:
  - Arpeggiator - helps generate arpeggios based on the base note
- Audio FX - helps create audio effect
  - EQ - when activate, it will display a small EQ graph in the strip that indicates the current setting
    - It controls the magnitude of sounds in different frequency
    - Select the top drop-down to choose preset EQ settings, then tweak based on the result
  - Amp Designer - change amp setting for guitar or bass audio track
    - Drag the point in front of the speaker diagram to change the position of the recording mic
    - In the drop-down below to change the model/amp/cabinet/mic type
  - Pedalboard - change the tone by changing the pedalbaord setting for guitar and bass

#### Mixer

- Mixer enables the adjustment and control of all channel strip from different track in one place
- Press `X` to open the Mixer panel, or `Command + 2` to open a separate mixer window
- Plug-in setting can be copied from one track to another in the mixer panel, by holding `option` key and dragging the plug-in to another track

### Record and Play Tracks

- Use lower buffer size in Audio setting to reduce recording latency
  - Lower buffer size consume more CPU power which is not suitable for computing intensive tasks
- In the recording preference, select 24-bit resolution for better quality and lower noise, unless storage is a concern
  - uncheck will result in a 16-bit resolution
  - `24-bit` resolution or depth means at any given time the sound can be sampled in one position of a 2^24 scale(2^24/2 step in both positive and negative direction) during the recording(analog to digital conversion) process
  - The noise is introduced by quantization error, including rounding errors and loss of precision introduced during audio processing
- From the top menu bar, select `File -> Project Settings -> Audio..` and select a sample rate for recording
  - High sampling rate comsume more computing power
  - The sampling rate options depend on the capability of the audio interface
  - Sample rate is proportional to the file size and 48kHz appears to be a good choice for having acceptable file size and sound quality
  - High pitch(higher frequency) instrument are more likely to benefit from higher sampling rate
- From the top menu bar, select `Preferences -> Recording..` and select `Create Take Folders` to enable take folders
  - take folder group additional recordings for the same track in a folder for further selection or processing
  - Additional recording will be kept and named `Take 2` below, select the take to use it
  - Double click the main sound track to collapse or expand the take folders
  - Drag a section of the unselected take to use that specific section on the main track, avoid starting the section on a high magnitude time frame for a smooth transition
  - Click the `A` icon on top of the main track and select `Flaten and Merge` to confirm the merge and delete all takes
- In the audio interface setting use instrument level input when connecting with an electrical instrument with Direct Injection or Direct Input (DI)
- One instrument can be recorded two times with each track pan to left max and right max to create high quality stereo tracks
- Press `R` button to start recording
- Press `Space` to stop recording, press again to play the recording, press again the reset the play head
- Press `C` to enable/disable loop playback, select a track section and press `Command` + `U` will enable loop on this section
- Hold `Command` and click the sound track section to activate the skip cycle mode.
  - the section's cycle bar will turn dark and the section will be skipped when playing in the future
  - `Command` and click again to deactivate
- Press `Command` + `Z` to undo recording

### Edit Tracks

- Zoom
  - `Command + Arrows` key to zoom the tracks
  - Hold `Shift` and press the bottom of the track header to set all other headers to the same size
  - `Z` auto zoom
  - Hold `Command` resize all track header to the same size
- Select a track header and press `delete` to delete
- MIDI tracks can be quantized by selecting `Quantize` option in the `Region` section on the Inspector Panel
  - Quantization adjust the note length to fit the specified unit note length
- One of the following panel can be opened at the bottom for selected track
  - Press `B` to open the Smart Control panel
  - Press `E` to open the Editor panel
- Repeat Track Sound
  - Recordings or Loops be extends by dragging its left border
    - Select the looped sound and press `Control + L` to convert loops to real copys
  - Select track sound and press `Command + R` to create a separated and duplicate recording after the selected one
- Snap mode can be selected in the track tool bar
  - Turn off snap mode to move tracks freely, or `Command + G`
  - Different snap mode can snap the pointer to different grid when dragging tracks
- Drag mode has:
  - `X-Fade` - Do x-fade when overlap
  - `no overlap`
- Select a drummer sound track section, in its setting panel, check `follow` beside `Kick & Snare` and select a track to let the drumer follow the kick and snare base on a certain audio recording
- Click Tools are used when mouse is clicked on the sound track
  - Click tools can be set for left click and `Command + Click` in the track tool bar
  - Right click can be set as another tool in `Preference->General..`, `Right Mouse Button` in the `Edit` tab
    - Make the Tool changes dynamically based a the click region(upper/lower part) on the track by selecting the click zone options
  - Press `T` to access all tools directly
  - Pointer Tool - Selection
    - Drag the track to move it
    - select and press `delete` to remove a clip
    - Drag from the track edge to trim the track
    - Hold option and drag the track to create a copy
    - `Control + Shift + Drag` from inner part to edge part will create a fade
      - The boundary of the fade region can be dragged and modified
      - Right click the fade region for more options
        - It supports tempo changes during fade
      - Drag the boundary inside of an adjacent clip will create cross fade
        - croos fade helps create a smooth transition between two clips
        - select multiple clips can create cross fade for all of them
  - Eraser Tool - Delete sections
  - Text Tool - Change section names
  - Scissors Tool- Split section into two based on the snap setting
    - Hold `option` and use scissors tool to split one region into multiple sections
  - Glue Tool - combine all selected sections into one
    - select section and press `J`(join function) will join all section into a separate audio file
  - Solo Tool - play selected region
  - Mute Tool - mute selected region
  - Zoom Tool - zooming
  - Fade Tool - fading
    - The same as `Control + Shift + Drag` when using pointer tool
  - Marquee Tool - selection regions within a clip
    - use pointer tool to select small region to trim it into a separate region

## Export the Project

- Select the track range and then press `Command` + `B` or `File` -> `Bounce` -> `Project or Section` from the top menu bar to export the music
- One or more desired output format can be selected
  - PCM - uncompressed
    - File Type: Split will separate the audio into left and right file, interleaved will combine those into one file
    - Dither is used to reduce background noise by adding a random noise
- `Realtime` Mode will bounce the music during playback, it is more accurate
- `Offine` Mode will be faster
