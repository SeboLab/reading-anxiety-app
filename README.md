Instructions for everything that we used to run the reading anxiety user study

1. App: The [code](https://github.com/SeboLab/reading-anxiety-user-study-tools/tree/main/reading-app) used in the tablets is uploaded on here! The corresponding RoS integration can be accessed [here](https://github.com/SeboLab/misty_reading)

2. Pipeline during the study:

  * Set up a monitor and connect it to the raspberry pi (keep in mind that you should plug in the pi after connecting the monitor since it might not detect new display inputs after being booted).
  * Connect your keyboard, mouse, and microphone to the pi as well
  * Login to the Pi using the password: mistyreading
  * Your tablets and pi should all be on the same wifi!
  * Once switched on run the following commands on the terminal (run each chunk of lines on a different terminal window)
      1. **Setting up dependencies**
         cd ~/catkin_ws && catkin_make
         source devel/setup.bash
         roscore
      2. **If running the robot condition, run the following commands to connect to Misty:**
          source devel/setup.bash
          rosrun misty_api main.py 192.168.1.XXX (whatever the last three digits are)
      3. **To connect with the tablet run:** ( you won't be able to connect with the tablet until you input the correct ip address of the pi into the tablet )
         source devel/setup.bash
         rosrun misty_reading tablet_node.py
      4. **For connecting to the correction manager(code can be accessed [here](https://github.com/SeboLab/misty_reading))** (run this chunk before using the tablet to connect with the pi)
         source devel/setup.bash
         rosrun misty_reading correction_manager.py <storyno1> <storyno2>
         
      *Once all this is setup, you'll have gone into a different page that will make you pick human vs robot condition! For human condition select the correct stories, and for robot you don't have to do anything beyond click on the button*
    
      5. **To connect to the trascription script**
         source devel/setup.bash
         rosrun misty_reading transcription_node.py
         (Important note: don't run this script unless the child has started reading! Also if it ever fails, it usually is due to your date and time not being synced)
      6. **To record audio**
         arecord name.wav
 
   * Open strava and connect heartrate monitor
   * Open anydesk on both the tablets and click on the windows on one of the boxes and then a pop up should appear on the other tablet with an Accept button! This should connect your two tablets!! (keep bluetooth on) 
