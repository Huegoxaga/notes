# Media

## Media Format

### Raster Image

### 2D Vector

### 3D Vector

### Audio

### Video

## FFmpeg CLI

- It is part of the FFmpeg project for handling multimedia files
- Visit the official website at `https://ffmpeg.org`
- It works on Linux, Windows, and Mac
- run `brew install ffmpeg` to install on MacOS
- `ffmpeg -i input.mp4 new.avi` convert `input.mp4` to `.avi`
- `ffmpeg -i input.mp4 new.gif` create `gif` from the video
- `ffmpeg -i <PathToMPD/M3U4> -codec copy output.mp4` download video stream
  - The link to the stream manifest file can be found using browser plugins
- `ffmpeg -i <InputFile> -q 4 output.avi` change the `avi` output quality setting to `4` the lower the number the better the quality, `50` results in a very low quality video
- `ffmpeg -i <InputFile> -crf 18 output.mp4` change the `mp4` output quality setting to `18` the lower the number the better the quality
- set output bitrates
  - `ffmpeg -i input.mp3 -b:a 320k output.mp3` convert the bitrate of the audia channel of a mp3 media file to `320k`
  - `ffmpeg -i input.avi -b:a 128k -b:v 1000k output.mp4` convert videos with exact bit rate for video and audio
- filters
  - `ffmpeg -i input.wav -filter:a "volumn=2" output.mp3` use the filter on the audio channel to double the volumn in the output `mp3` file
  - `ffmpeg -i input.wav -filter:a "channelmap=0-0|0-1" output.mp3` use the filter on the audio channel to copy sound track from left channel `0-0` to the right channel `0-1`
  - `ffmpeg -i input.mp4 -filter:v "crop=w=1290:h=960" output.mp4` use the filter on the video channel to crop the video at the center
  - `ffmpeg -i input.mp4 -filter:v "crop=w=1290:h=960:x=0:y=0" output.mp4` use the filter on the video channel to crop the video with top left point located at point `(0, 0)`
    - `in_h` and `in_w` are variables that are available as input, arithmetic symbols can be used with the variables
  - `ffmpeg -i input.mp4 -filter:v "scale=w=2/3*in_w:h=-1" output.mp4` use the filter on the video channel to scale the output width to two third of the original and auto adapt the height to keep the same ratio
  - `ffmpeg -i input.mp4 -filter:v "rotate=90*PI/180" output.mp4` rotate the video 90 degrees clockwise, angle is in radian
  - `ffmpeg -i test.mkv -f ffmetadata metadata.txt` save metadata into a text file

## youtube-dl

- It is a CLI tool for downloading youtube videos
- run `youtube-dl "<URL>"` to download the video in highest quality by default

## Mediainfo

- It can be used to display media information
- Visit the official website at `https://mediaarea.net/en/MediaInfo`
- run `brew install mediainfo` to install the cli tool on MacOS
- run `mediainfo <PathToFile>` to view the video details
