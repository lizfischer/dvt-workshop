# dvt-workshop


## Setup
### Downloading workshop materials
Make sharedfolder
download zip, put in sharedfolder

### Running docker
Open Terminal (Mac) or Command Prompt (Windows)
```cd ``` to your Desktop. Then do:
```
docker run --name dv -ti -p 8000:8000 --volume path/to/folder/:/sharedfolder/ hipstas/dv bash
```
You're now in the terminal of the docker container. To get into the shared folder, do
``` cd /sharedfolder/```

## Running DVT on a video clip
 ```python -m dvt video-viz video.mp4```

## General Tips
If it looks like DVT has stopped running (i.e. the number has been stuck for a while), try pressing an arrow key while in the command window. Sometimes the status bar just hasn’t updated and needs a little nudge to wake up.

## Viewing Output
```
python -m http.server --directory dvt-output-data
```
Open localhost:8000 in browser
 
## Shot Length
http://www.urbanfox.tv/creative/shotsizes.html#vls

## Face recognition
```
python -m dvt video-viz <path to file> --path-to-faces=<folder with faces>
```

Example:
```
python -m dvt video-viz SpeedShortTrailer.mp4 --path-to-faces=faces/speed/clip_faces/
```
