# dvt-workshop


## Setup
### Downloading workshop materials
Download this repository using the green "Clone or Download" button. Unzip the folder on your desktop. 

### Running docker
If this is the first time you're using the hipstas/dv docker image, get it by doing:
```
docker pull hipstas/dv
```
If this is *not* the first time you've done this, you may get an error that a container called dv already exists. Remove it by doing
```
docker rm -f dv
```
#### Mac
Open Terminal 
``` 
docker run --name dv -ti -p 8000:8000 --volume ~/Desktop/dvt-workshop-master/:/sharedfolder/ hipstas/dv bash
```

#### Windows
Open Command Prompt 
```
docker run --name dv -ti -p 8000:8000 --volume C:/Users/<yourusenamehere>/Desktop/dvt-workshop-master:/sharedfolder/ hipstas/dv bash
```

#### All OSes
You're now in the terminal of the docker container. To get to the workshop materials, do
`cd /sharedfolder/`


## General How-to
### Running DVT on a clip
In the terminal window, run the following command, changing `video.mp4` to whatever clip you want to run.
 `python -m dvt video-viz video.mp4`
 
For example:
`python -m dvt video-viz clips/very-short/canon_clip.mp4`

#### Hot tip
If it looks like DVT has stopped running (i.e. the number has been stuck for a while), try pressing an arrow key while in the command window. Sometimes the status bar just hasn’t updated and needs a little nudge to wake up.

### Viewing Output
The `video viz` pipeline we're using generates a website with which to view outputs. To view this website, run the following command:
```
python -m http.server --directory dvt-output-data
```
Then go to [localhost:8000](http://locahost:8000/) in your web browser.
 
## Tasks
1. Using the general instructions above, run DVT on a clip or two from the clips folder. Because DVT takes a little while to run on longer clips, you may want to try something from clips/very-short for your first time. 

2.
 
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
