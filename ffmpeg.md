---
created: 2023-12-25
tags:
  - ref
---
## Presents 
- For applying in Batch:
`for %f in (*.ext) do ffmpeg -i "%f" [command] "e-%~nf.ext"`
- trim:
`ffmpeg -i file.ext -ss 00:00 -to 00:00 -c copy file.ext`
- reduce video size: 
`for %f in (*.mp4) do ffmpeg -i "%f" -crf 28 "e-%~nf.mp4"`
- audiobook:
`for %f in (*.mp3) do ffmpeg -i "%f" -c:a libopus -b:a 48k "e-%~nf.opus"`
- reduce images size: 
`for %f in (*.jpg) do ffmpeg -i "%f" -q:v 3 "e-%~nf.jpg"`

- Watermark:
`ffmpeg -i input.mkv -i watermark.png -filter_complex "overlay=50:50" output.mkv`
- Chroma Key:
`ffmpeg -i input.mkv -c:v vp9 -filter:v "chromakey=0x00ff00:0.1:0.2" output.webm`
- Overlay Videos:
`ffmpeg -i input.mkv -i input2.mkv -filter_complex "[0:v][1:v] overlay=25:25" output.webm`

## Commands
- base command: 
`ffmpeg -i input.ext output.ext`
- copy metadata: `-map_metadata 0`
- VF:
	- resizing: `-vf scale=[scale]` W:H or -1 to auto calculate
	- Cropping: `-vf crop=[W:H:x:y]`
	- brightness and contrast: `-vf eq=brightness=0.06`
	- Rotating: `-vf "transpose=1"` 
	- Grayscale: `-vf format=gray`
	- combine: `-vf "scale=1280:-1,crop=1280:720"`
- image quality: `-q:v [1-31]`
- video quality: `-crf [18-51]`
- Trim Video:
	- start time: `-ss`
	- duration relative to start: `-t`
	- end time: `-to`
	- copy codec: `-c copy`
- video codec: `-c:v [video.codec]` "libx265" "copy"
- audio codec: `-c:a [audio.codec]` "libopus"
- video bitrate: `-b:v [video bitrate] `
- audio bitrate: `-b:a [audio bitrate]`
- FPS: `-r [fps] `
- resolution: `-s [resolution] `
- no video: `-vn`

