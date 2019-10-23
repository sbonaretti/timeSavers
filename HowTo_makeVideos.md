# How To: Make videos  

Nice youtube channel: https://www.youtube.com/channel/UCUyUBvmOh4JGVmVIigbYG7A/videos   
- Record screen using QuickTime: https://www.youtube.com/watch?v=mLyPrblmPp4 
  - File -> New screen recording
- Edit video using iMovie  
  - Projects -> Click on the `+`  
  - Resolution is determined by the first video or photo in the timeline (see video: https://www.youtube.com/watch?v=eL94evs-k0g)
  - Drag and drop videos  
  - To split video in parts:   
    - Position the line to the place of interest
    - `command` + `b`    
  - Reduce background noise:  
    - Equalizer (histogram) icon
    - Reduce background noise (play with the %) + Equalizer: Voice Enhance
  - To save: icon top-right -> file


## To record terminal  (not used)

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

