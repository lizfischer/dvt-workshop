# dvt-workshop
Introductory workshop for Distant Viewing Toolkit

## Setup
 
## Running DVT on a video clip
 
## Viewing Output
```
python -m http.server --directory dvt-output-data
```
Open localhost:8000 in browser
 
## General Tips
If it looks like DVT has stopped running (i.e. the number has been stuck for a while), try pressing an arrow key while in the command window. Sometimes the status bar just hasn’t updated and needs a little nudge to wake up.

## Face recognition
DVT can do some basic facial recognition! All it needs is a folder with images of people’s faces with the name of the person as the file name. To run DVT with face recognition:
```
python -m dvt video-viz <path to file> --path-to-faces=<folder with faces>
```

For example
python -m dvt video-viz clips/SpeedShortTrailer.mp4 --path-to-faces=face/speed/clip_faces/
