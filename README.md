
[Distant Viewing Lab](https://www.distantviewing.org/)

[Distant Viewing Toolkit documentation](https://distant-viewing.github.io/dvt/index.html)
## Setup
### 1. Downloading workshop materials
Download this repository using the green "Clone or Download" button. Unzip the folder on your desktop. 

### 2. Running docker
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
#### Windows 10 (Docker Desktop)
Open Command Prompt 
```
docker run --name dv -ti -p 8000:8000 --volume C:\Users\<yourusenamehere>\Desktop\dvt-workshop-master\:/sharedfolder/ hipstas/dv bash
```
#### Windows 7 (Docker Toolkit)
Caution: this material is untested on Docker Toolkit for Windows (the pre-cursor to Docker Desktop).

Open Command Prompt 
```
docker run --name dv -ti -p 8000:8000 --volume //c/Users/<yourusenamehere>/Desktop/dvt-workshop-master/:/sharedfolder/ hipstas/dv bash
```

#### All OSes
You're now in the terminal of the docker container. To get to the workshop materials, do
`cd /sharedfolder/`. You should now be able to see all the workshop materials in the folder by doing `ls`.

## 3. General How-to
### Running DVT on a clip
In the terminal window, run the following command, changing `video.mp4` to whatever clip you want to run.
```python -m dvt video-viz video.mp4```
 
For example:
```python -m dvt video-viz clips/very-short/canon_clip.mp4```

### Viewing Output
The `video viz` pipeline we're using generates a website with which to view outputs. To view this website, run the following command:
```
python -m http.server --directory dvt-output-data
```
Then go to [localhost:8000](http://locahost:8000/) in your web browser.
 
### Stopping Server 
Once you've started the server, you have to stop it before running DVT on a different clip. To stop the server, do `ctrl C` in the terminal window. Only do this once! If you do it multiple times, you may exit the docker container and need to restart it. 
 
### Face recognition
To run DVT with face recognition, supply a folder containg one picture of every person you would like it to look for. The name of the image should be the person's name.
```
python -m dvt video-viz <path to file> --path-to-faces=<folder with faces>
```

Example:
```
python -m dvt video-viz SpeedShortTrailer.mp4 --path-to-faces=faces/speed/clip_faces/
``` 
 
## 4. Activities
#### 1. Run and view basic DVT output
Using the general instructions above, run DVT on a clip or two from the clips folder. Because DVT takes a little while to run on longer clips, you may want to try something from clips/very-short for your first time. View the output in your browser and familiarize yourself with the interface.

#### 2. Face recognition 
DVT doesn't yet include face recognition results in the website visualization, so we've pre-run face recognition on a shortened version of the Speed trailer. We ran DVT on the clip 3 times with 3 different sets of labeled images-- 1) screenshots of the actors' faces from the clip, 2) pictures of the actors not from the film, and 3) pictures where the actors' appearances are substantially different in some way (either older/younger, no facial hair, glasses, etc.) 

1. Open the `face-recognition-demo` folder.
2. Watch the video clip `Speed.mp4`
3. Examine the contents of the `faces` folder to see the different seed image that were used.
4. Open `face-recognition-demo/dvt-output-data/img`. For each of the three folders within (Speed_Clip_Faces, Speed_Hard_Faces, and Speed_Outside_Faces), explore the contenxt of the `faces` folder. 

##### Questions
* Who got recognized consistently? Who didn't?
* Did the difference of seed image make a difference or not? In all cases, or only some? 
* What suprised you about these results?

#### 3. Viewing a larger dataset
Because DVT takes a while to run, we prepared an output site with 20 film trailers, 10 string performances, and 10 protest videos. To view the full output:
1. In the Docker terminal window, do `cd /sharedfolder/` if you aren't there already
2. Run `python -m http.server --directory full-data-output` 
3. Open [localhost:8000](http://locahost:8000/) in your web browser.

We've also pulled select data from the JSON files DVT produces for every video and compiled them into a `AllData.csv` for easy viewing. This file contains: video name, number of shots, number of shots with people, objects and people detected, avgerage number of people per shot, most common shot length, and average shot duration in seconds.

## 5. Discussion Questions
As you do the above activities, consider the following questions based on what role you were assigned:

### Everyone
* What uses for Distant Viewer can you see or imagine, having looked at it from another profession’s point of view?
* What additional questions would you want to ask of this kind of data?
* What couldn’t you do in DVT that you wish you could?
* Expanding beyond film studies, what areas of scholarship can you imagine benefitting from “distant viewing”?
* Do you think DV could be used for facial recognition, such as for scanning large quantities of security footage? What do you think would be the bigger implications of that?
* Can you think of other professions or activities beyond the academy and our sample roles which might find DV useful? 
* What are the things that you did not discover when you watched the clips with your own eyes instead of with the DV tools?

### Film Scholar 
* What data that DVT can provide might be useful in your work? 
* What kind of expertise or skill sets do you think you need in order to interpret the data and generate meaningful questions? In other words, what might constitute the knowledge gap for you?
* How can you connect the data output with critical questions? 

### Archivist 
* How might you apply DV in your everyday work? What concerns might you have about using it?
* What kinds of data would be useful to have for video collections? What kinds of data can DVT provide, and what can’t it?
* How could DVT be useful for still images?

### Law Enforcement 
* What data that DVT can provide might be useful in your work? 
* Are there other kinds of data you would like to get out of DV? 
* If you don’t find DV very helpful, would you still like to develop the concept further and produce something related but different? 

*****

#### Notes
##### Shot Length
One of the things DVT measures is "shot length." Shot length is not the same as shot duration; it is a measure of how big the field of view is. There are 7 levels:
1. Very Long Shot (VLS)
2. Long Shot (LS)
3. Medium Long Shot (MLS)
4. Mid Shot (MS)
5. Medium Close Up (MCU)
6. Close Up (CU)
7. Big Close Up (BCU)

You can read more about these here: https://en.wikipedia.org/wiki/Shot_(filmmaking)#By_field_size

##### Why isn't the status bar moving?
If it looks like DVT has stopped running (i.e. the number has been stuck for a while), try pressing an arrow key while in the command window. Sometimes the status bar just hasn’t updated and needs a little nudge to wake up.

