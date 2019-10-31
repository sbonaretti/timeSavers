# How To: Make videos  

Nice youtube channel: https://www.youtube.com/channel/UCUyUBvmOh4JGVmVIigbYG7A/videos  

## Recording: QuickTime
- Info: https://www.youtube.com/watch?v=mLyPrblmPp4 
  - File -> New screen recording
- Note: iMovie makes the movie in 4:3 aspect ratio or 16:9 aspect ratio, so record with this aspect ratio
  
## Editing: iMovie
  
- Projects -> Click on the `+`  
- Resolution is determined by the first video or photo in the timeline (see video: https://www.youtube.com/watch?v=eL94evs-k0g) 
  - As first item, put a 4K res image, then the first video. Then delete the 4k image - iMovie keeps in memory 4K as the video resolution
- Drag and drop videos  
- To split video in parts:   
  - Position the line to the place of interest
  - `command` + `b`    
- Reduce background noise:  
  - Equalizer (histogram) icon
  - Reduce background noise (play with the %) + Equalizer: Voice Enhance
- Aspect ratio: if videos are recorded with different aspect ratios, crop the larger videos to the aspect ratio of the smallest one
- To save: icon top-right -> file


## Publishing: YouTube  
- Sign in in studio.youtube.com with the google account  
- Click on the camera icon with a + in the top-right of the page -> Upload video (Beta) -> Fill out info
- Parameters to select: 
  - Visibility: Unlisted. The video is uploaded at low res. It takes 2-3 hours before the video is available at high res. To check whether it is ready (https://support.google.com/youtube/answer/71674?hl=en):  
    - Go to Videos (left navigation bar) and click on the video 
    - Click on the video link under the video preview on the right to open the video's watch page (i.e. the youtube page where the video is displayed)
    - Click on the settings gear on the video and see whether several quality options appear. If so, the video is ready to be made public 
- Note: It is not possible to replace a video


## Recording terminal  (not used)

Asciinema saves in `.cast`, which needs to be transformed to `.gif` and then to `.mp4`. 

- Asciinema: https://asciinema.org/  
- Installation:    
  ```
  pip install asciinema
  ```  
- Start recording:  
  ```
  asciinema rec /path/filename.cast
  ```  
- Stop recording:   
  ```
  exit
  ```  
- Save: 
  ```
  crtl + c
  ```  
- Edit:  
  The `.cast` file is a `.json` file, so it can be opened with Atom and edited  

