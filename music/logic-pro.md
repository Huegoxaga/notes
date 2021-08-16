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
- Right click the control bar and select cutomize to add frequently used tool icons

## Creating Projects

- Press `Shift` + `Command` + `N` to create a new empty project
- Press `Command` + `N` to create a new project from template

### Project Setup

- The project interface will be shown after the first track is created
- `LCD` display in the centre of the top control bar can be used to setup project tempo and time signature
  - Open the drop-down and select `Custom` to display more info
- Adjust the master volumn on the top control bar
- `Shift + Option + A` opens the MIDI assignment window, that can be used for MIDI input setup
  - Select `Learn Mode` and make software control changes, then the type of control will be recogized for external device assignment

### Create Tracks

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
- Audio track is in blue, drum track is yellow, MIDI track is green
- When the project is opened, a track can be created by clicking the plus button(`Option + Command + N`) above the track headers
- Tracks can be duplicated by selecting and clicking on the duplicate button above the track headers
- Double clicking on the empty space below track header to duplicate a selected track
- Clicking on the Global Track icon above track headers, or press `G` key to open `Arrangement` info, section `Marker`, Time `Signature`, `Tempo` panel and click `+` icon to insert them as a global track on top of all tracks
  - The Global `Tempo` track can be used to speed up or slow down the project overtime
- Press `O` to open the Apple Loop Browser, to filter(based on instuments, genres, moods) on the top and click to preview loops, then drag the loop to an empty track area to create loop track
  - Loops with green icons are MIDI loops
  - Loops with blue icons are audio loops
  - Loops with yellow icons are drum loops
- Press `Option + C` or go menu bar `View -> Show Color` to color the selected tracks

### Save a Project

- A project can be saved as a single package or a project folder
- Only Audio Files are required to be copied
  - All project related files need to be copied when the project will be moved to another computer

## Project Interface

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

## Recording

- Use lower buffer size in Audio setting to reduce latency in the recorded track
  - Turn on the low latency mode to reduce the latency further by clicking the low lantency icon on the control bar
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
  - use `<` and `>` key or `Shift + <` and `Shift + <`(1 bar at a time) to move the play head
- Press `K` to open and record with the typing keyboard, it is a software typing keyboard
- Press `C` to enable/disable loop playback, select a track section and press `Command` + `U` will enable loop on this section
- Hold `Command` and click the sound track section to activate the skip cycle mode.
  - the section's cycle bar will turn dark and the section will be skipped when playing in the future
  - `Command` and click again to deactivate
- Press `Command` + `Z` to undo recording
- The `Catch Playhead` switch is located on the tool bar, at the left of the `Pointer Tool` icon
- Select a track then press `A` to enable automation mode, it can be used to record volumn changes, pedal board changes etc
  - click on the track and drag the volumn line to add dynamic volumn control
  - use the drop-down in the track header below the automation track switch to select the type of control that be to be recorded
  - The changes can be made using mouse or external MIDI controller during recording
  - In the track header, four automation modes are available:
    - Read - only read data
    - Touch - write data, cut of the changes when not receiving signal
    - Latch - write data, hold the changes when note receiving signal
    - Write - similar to Latch but overwrite all other automation signal

## Editing

- Zoom
  - `Command + Arrows` key to zoom the tracks
  - Hold `Shift` and press the bottom of the track header to set all other headers to the same size
  - `Z` auto zoom
  - Hold `Command` resize all track header to the same size
- Select a track header and press `delete` to delete
- Tracks can be quantized by selecting `Quantize` option or change pitch or add fade in or fade out(more) in the `Region` section on the Inspector Panel
  - Quantization adjust the note length to fit the specified unit note length
  - Audio track need to enable `Flex Time` first
  - Drag the content under `Transpose` and `Fine Tune` to change the pitch
- One of the following panel can be opened at the bottom for selected track
  - Press `B` to open the Smart Control panel
  - Press `E` to open the Editor panel
- Repeat Track Sound
  - Recordings or Loops be extends by dragging its left border
    - Select the looped sound and press `Control + L` to convert loops to real copys
  - Select track sound and press `Command + R` to create a separated and duplicate recording after the selected one
- Track pitch change be changed in the following ways
  - Drag tempo value under `LED` section
  - Drag the tempo value in the `Global Track`'s tempo track
  - Press `D` to open the list editor and change tempo in the `Tempo` panel
- Snap mode can be selected in the track tool bar
  - Turn off snap mode to move tracks freely, or `Command + G`
  - Different snap mode can snap the pointer to different grid when dragging tracks
- Drag mode has:
  - `X-Fade` - Do x-fade when overlap
  - `no overlap`
- Select a drummer sound track section, in its setting panel, check `follow` beside `Kick & Snare` and select a track to let the drumer follow the kick and snare base on a certain audio recording
- Right click a drummer region and select `Convert -> Convert to MIDI Region` for detailed editing
- Right click on empty track can create a MIDI region, so it can be edited using the Piano Roll Editor
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
    - `Command + J` will join all selected tracks into a single separate file
  - Solo Tool - play selected region
  - Mute Tool - mute selected region
  - Zoom Tool - zooming
  - Fade Tool - fading
    - The same as `Control + Shift + Drag` when using pointer tool
  - Marquee Tool - selection regions within a clip
    - use pointer tool to select small region to trim it into a separate region
- Flex time tool - it is used to adjust the timing(quantize) of the audio recording grid by grid
  - Click the Flex time icon on the tool bar or press `Command + F` to display the Flex time icon on the track header for each track, then click on the flex time icon on the track header to enable flex time for that track
  - Select the apropriate flex mode on the track header
    - Automatic - not recommanded, sometimes will have bad results
    - Polyphonic - for instrument play more than one note at the same time
    - Monophonic - for instrument play one note at a time, use polyphonic when the result doesnot sound good
    - Rhythmic - for percussion instruments
    - Slicing - for drums
    - Speed - for special effect
    - Tempophone - for special effect
    - Flex Pitch - it is used to adjust to pitch or vocal recording, once select double clicking the region to open the track editing panel at the bottom
      - Select all and scale quantize the voice onto a selected scale using the quantize tool on the left panel
      - Slide the pitch correction slider up to increase the correction level
      - Double click the yellow timeline to play
      - There are six properties the tool can tune by dragging one of the six dots around the pitch bar
        - Fine Pitch(upper middle dot) is the pitch of the voice in cent(one cent in 1% of a semitone)
        - Vibrato(lower middle dot) is the variance of the pitch in percentage
        - Front Pitch Drift(upper left dot)
        - End Pitch Drift(upper right dot)
      - toning will reduce the tonal quality
      - Use scissors tool to cut a note into two
      - Use glue tool to join separate notes into one
      - The length of each note can also be adjusted by dragging
  - make sure the `complex` checkbox under the track option in the inspector is checked for a better result
  - brighter color grid means the time is compressed, grey section means time is stretched, original color means the time length is close to its original
  - The program will auto detect the beat on the audio track and display a flex time marker on the transient for on each grid
  - Select the audio track and use the quantize tool to adjust the timing for each grid
  - drag the flex marker to adjust manually
  - click on the sound wave to create the flex marker
  - Drag the Eraser Tool or click the delete icon above the flex marker to delete the flex marker
  - Use join track to render flex edit in place
    - For a track with single region using bounce tool or create a small region to join at the end, then delete it
  - Disable flex time when done
- Increase the buffer size to max and turn off the low latency mode before vocal editing to improve performance
- Tracks from one instrument can be copied and pasted to another
  - Drum Track will be converted if it is being pasted into a MIDI track
- Select multiple tracks, press `Command + Shift + D` or `Track -> Create Track Stack...` from the top menu bar, then select create `Summing Stack` to add effects to multiple stacks
  - Summing Stack has all the feature as an individual track, e.g. mixing

### Audio Editor

- Select Audio region and press `E` to open the editor

#### File View

- Function Drop-down
  - Select `Reverse` to reverse the file

### Piano Roll Editor

- It is used to edit MIDI region
- It can be opened by press `P`, or double click on the MIDI region to open the editor at the bottom
  - `Command + 4` to open it in a separate window
- It has seperate mouse tools
  - Pointer tool can be used to drag notes around
    - Use `Option + Arrow` can move selected notes around
    - Use `Option + Shift + Arrow` can move notes by one octave
  - Pencil tool can be used to insert notes by clicking on the desired location
  - Brush tool can insert multiple notes by dragging the mouse across
  - Velocity tool can be used to adjust the velocity of selected notes by dragging up or down
    - When select multiple notes the velocity increase based on its original value
    - Hold `option` key then drag the mouse to make all notes change with the same velocity value
    - Notes with higher velocity will be more red
    - Velocity slider on the left panel set a `1-127` value for each notes
    - Velocity stores a certain quality of the note and it is used to adjust the volumn most of the time
    - when recording using MIDI keyboard, it is related to the input speed
- To quantize a recorded track, `command + A` to select all notes, and click `Q` icon in the Time quantize tool on the left panel after select the correct base note length
- `Edit -> Trim -> Note end to Following Notes(Force Legato)` or press `Shift + \` to extend all notes and fill the gap until a note reaches the next one
- On the top tool bar of the editor, click the MIDI in icon, then MIDI input from connected MIDI device or software keyboard will be recorded in the editor
  - Click the MIDI out button to mute during note editing
- From the top menu bar, `Window->Show Step Input Keyboard` or press `Option+Command+K` to open the Step Input Keyborad, then multiple note can be entered for one step at a time
  - Set the step interval by clicking the coresponding note type
  - play head will proceed to the right after each input

### Score Editor

### Step Editor

## Mixing & Mastering

### Plug-ins

- They are located in the channel strip
- They can be turn off by clicking the power button or select `No Plug-in` in the drop-down
- Plug-in effects are added to the sound in order, from top to bottom
- Tuner - helps tune the input instrument for audio tracks, or select the `fork` icon on the top control panel
- MIDI FX - helps create MIDI effect using one of the following plug-in:
  - Arpeggiator - helps generate arpeggios based on the base note
- Audio FX - helps create audio effect
  - EQ - when activate, it will display a small EQ graph in the strip that indicates the current setting
    - The channel EQ has 8 filters to change the sound, each fileter is represented in different color
    - It controls the magnitude of sounds in different frequency
    - Select the top drop-down to choose preset EQ settings, then tweak based on the result
  - Amp Designer - change amp setting for guitar or bass audio track
    - Drag the point in front of the speaker diagram to change the position of the recording mic
    - In the drop-down below to change the model/amp/cabinet/mic type
  - Pedalboard - change the tone by changing the pedalbaord setting for guitar and bass
- Click the empty space below to add more effect plugins

#### Third Party Plugins

- They can be install be move the `.vst` file to the `/Library/Audio/Plug-Ins/VST` folder and `.component` file to the `/Library/Audio/Plug-Ins/vst/Components` folder in `Library/Plug-ins` folder
  - If download `.dmg` files install them directly
  - Go to `Preference -> Plugin Manager...` from the top menu to view plugin status
  - Restart `Logic Pro` to load the new plugin
- Lists of third party plugins
  - [U-HE TYRELLN6](https://splice.com/plugins/1837-tyrell-n6-vst-au-by-u-he) - Synthesizer
  - [iZotope Vinyl](https://www.izotope.com/en/products/vinyl.html) - simulator adds the dust, scratches, warp, and mechanical noise
  - [Camel Crusher](https://www.audiopluginsforfree.com/camelcrusher/) - compressor that add distortion
  - [Melda Bundle](https://www.meldaproduction.com/MFreeFXBundle) - plugin bundle
  - [Iowa Alto Flute](https://vst4free.com/plugin/2327/) - sampled alto flute from the University of Iowa Electronic Music Studios
  - [Span Voxengo](https://www.voxengo.com/product/span/) - spectrum analyzer
  - [LoadMax](https://loudmax.blogspot.com) - It is a Look-Ahead Brickwall Loudness Maximizer Plugin with a clean transparent sound. It is designed to retain the original character of the music as much as possible even at high compression levels

### Mixer

- Use Mixer to do mixing after the tracks are fully edited
  - Check the `Mix->Pre-Fader Metering` to see the input level on the meter before it reaches to the fader volumn control
  - Before the mixing, increase the buffer size to biggest to increase performance
  - For each channel, mixing includes:
    - adjusting `EQ`, increase or decrease the output for different instrument at different frequency based on its tone and focus
    - adding `Compressor`, `Envoloper`
    - Adjust `Pedal`, `Amplifier`, `Exciter` for guitar and bass
    - adding `reverb` and/or `delay` and/or `spreader` each by send a channel strip signal to a new bus, add effects on that channel with small volumn as a reverb/delay sound source from a room
      - right click the new channel strip for the new bus, then generate a track for further processing, e.g. creating track stack or record automation controls
      - different tracks can send signals to the same new bus to get the same effect
    - Adding `Multipressor` for harmony vocal track stack, to control volumn based on pitch
    - Adjust pan
    - Control volumn that allows the master output keeps around at least 6dB below the cliping level(red line)
    - Adding or adjust the volumn automation
- Use Mixer to do mastering after mixing - mastering focuses on overall control of the stereo out, it includes:
  - Adding overall `EQ`, e.g. using `Linear Phase EQ` to cut low and boost high(not too much)
  - Adding `MultiPressor`
  - Adding `Limiter` and then `Meter`
  - Readjust by monitoring with other output devices for final output, then ready for bouncing
- Click the drum plugin and select multi-output and click the plus buttom below the meter to add multiple channels to take input from different part of the drum, then the sound from each part can be modified separately by using plugins
  - to add overall effect, create a track stack
- Mixer enables the adjustment and control of all channel strips from different track in one place
- Press `X` to open the Mixer panel, or `Command + 2` to open a separate mixer window
- Plug-in setting can be copied from one track to another in the mixer panel, by holding `option` key and dragging the plug-in to another track

## Export the Project

- Select the track range and then press `Command` + `B` or `File` -> `Bounce` -> `Project or Section` from the top menu bar to export the music
- One or more desired output format can be selected
  - PCM - uncompressed
    - File Type: Split will separate the audio into left and right file, interleaved will combine those into one file
    - many music streaming platform only support `16bit` bit depth and `44100` sample rate
    - Dither is used to reduce background noise by adding a random noise, it is used when boucing bit depth is lower(16bit) than the recording bit depth(24bit)
- Bounce Mode
  - `Realtime` Mode will bounce the music during playback, it is more accurate
  - `Offine` Mode will be faster
- `Normalize` is used to prevent cliping when the mastering step is skipped

## Devices

### Mic

- Microphones have comparatively small output voltages, on the order of thousandths of a volt (0.001V) ranging up to tenths of a volt (0.1V).
  - dynamic and ribbon mics are usually low-output Mics
  - Condenser mics are usually high-output Mics
- Preamp, amp or audio interface can be used to boost mic level output to line level
- Mics use balanced(grounded) `XLR` cable

### Electric Instruments

- Electronic Instrument - A distinction can be made between sound produced using electromechanical means (electroacoustic music) and that produced using electronics only
  - Electromechanical instruments have mechanical elements that produce the sound, then further work with electric elements, such as magnetic pickups, power amplifiers and loudspeakers
    - telharmonium(Dynamophone) - electrical organ, the first electromechanical musical instrument
    - Hammond organ - electrical organ
    - electric piano
    - electric guitar
  - Pure electronic instruments do not have vibrating strings, hammers or other sound-producing mechanisms
    - theremin - is an electronic musical instrument controlled without physical contact by the thereminist (performer). It is named after its inventor, Leon Theremin, who patented the device in 1928
    - synthesizer - it is an electronic musical instrument that generates audio signals. Synthesizers generate audio through methods including subtractive synthesis, additive synthesis, and frequency modulation synthesis. These sounds may be shaped and modulated by components such as filters, envelopes, and low-frequency oscillators, a synthesizer can be:
      - played with keyboards
      - controlled by sequencers - a device or application software that can record, edit, or play back music
      - controlled by software
      - played with other instruments via MIDI
    - computer
- A electric instrument will output either digital signal through MIDI port or analog singal through instrument level output port

#### MIDI

- MIDI is a technical standard for connecting electronic musical instruments
- Data transmitted by MIDI is attached with a channel info from 1 to 16, only devices or functions mapped with a certain channel will read data related to that channel, so MIDI cable can contain information for a max of 16 instruments
- MIDI transmit five types of message
  - Channel Voice transmit real-time performance data over a single channel, it has:
    - `note-on` messages contain
      - a MIDI note number(0-127) - 128 values assign to notes from C1 to G9
      - a velocity value(1-127) - indicates how forcefully the note was played
      - the channel number
    - `note-off` messages that end a note
    - program change messages that change a device's patch
    - controller change messages that allow adjustment of an instrument's parameters.
  - Channel Mode
  - System Common
  - System Real-Time
  - System Exclusive

#### Instrument Level Output

- The output voltage is lower than line input and higher than mic input
- A preamplifier or audio interface is required to bring the signal up to line level
  - A DI box can be used to convert instrument level down to mic level
- It uses unbalanced `1/4` inch or `1/8` inch `TR`(tip and sleeve) cable

### Preamplifier

- Line level connectors have balanced `TRS`(Tip, Ring, Sleeve) connectors with two black rings or unbalanced `TS`(Tip, Sleeve) connectors with one black ring
- Line level connectors have `1/8` inch connector and `1/4` inch connector
- It outputs line level signal to amplifier
  - Consumer line level is rated around -10dBV e.g. a CD player uses this signal to power the headphone
  - Professional line level is rated around +4 dBu and can be found in equipment like mixing desks, preamplifiers, and signal processing equipment

### Amplifier

- It takes input from preamplifier or sometimes includes the function of a preamp, then it powers the speaker with speaker level output

## Tools

### Spleeter

- Spleeter is Deezer source separation library with pretrained models written in Python and uses Tensorflow. It makes it easy to train source separation model (assuming you have a dataset of isolated sources), and provides already trained state of the art model for performing various flavour of separation :
  - Vocals (singing voice) / accompaniment separation (2 stems)
  - Vocals / drums / bass / other separation (4 stems)
    - 2 stems and 4 stems models have high performances on the musdb dataset
  - Vocals / drums / bass / piano / other separation (5 stems)
- Installation
  ```sh
  # install using conda
  conda install -c conda-forge spleeter
  # download an example audio file (if you don't have wget, use another tool for downloading)
  wget https://github.com/deezer/spleeter/raw/master/audio_example.mp3
  # separate the example audio into two components
  spleeter separate -i audio_example.mp3 -p spleeter:2stems -o output
  ```
