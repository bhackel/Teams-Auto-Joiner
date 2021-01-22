# Teams-Auto-Joiner-BCP

Modified to work with Bellarmine College Preparatory meetings only.

- [Prerequisites](#prerequisites)
- [Configuration options](#configuration-options)
- [Run the script](#run-the-script)

Python script to automatically join Microsoft Teams meetings.
Automatically turns off your microphone and camera before joining. Automatic login and blacklist can be set in the config file.

Always joins the newest meeting and leaves either after a specified time, if you are the last person in the meeting, or only if a new one is available (see [Configuration options](#configuration-options) for more information).
The original creator made a short tutorial video on how to setup the bot: https://youtu.be/YgkSOqfIjf4


## Prerequisites  
  
 - Python3 ([Download](https://www.python.org/downloads/))  
   
## New Config options  

- **member_interval:**  
Delay in seconds between checks for current member count and meeting status. Number must be 0 or greater. 

- **join_early_offset:**  
Seconds early that the program will join the meeting. Say class starts at 12:20, set at 60 seconds, it will join at 12:19.

- **auto_leave:**  
Will constantly monitor the number of meeting members to automatically leave when it is below a threshold. Disabling this does not stop auto_leave_after_min from leaving.
The number is specified by auto_leave_count, and the delay is specified by member_interval.  

- **auto_leave_count:**  
Maximum number of people in meeting to trigger an automatic leave. Must be 2 or greater  

- **auto_leave_blacklist_re:**
If meeting title matches a regular expression and auto_leave is enabled, it will not be automatically left.
Leave empty to automatically leave all meetings.
Useful if the class uses breakout rooms, since they will interfere with meeting member count.

## Configuration options  
  
- **email/password:**  
The email/password of your Microsoft account (can be left empty if you don't want to automatically login)  

- **run_at_time:**  
Time to start the script at. Input is a string of the hour and minute in 24h format, if you want it to start immediately leave this empty. 
If a time before the current time is given, the next day is used. Also make sure that you entered your email and password.
For example, if you want the script to start searching meetings at 6 in the morning on the next day, you would input `06:00` in the config.

- **random_delay:**
If true, adds a random delay (10s-30s) before joining a meeting. Can be useful so the bot seems more "human like".
Not very applicable since it does not really matter.

- **check_interval:**
The amount of seconds to wait before checking for meetings again. Number must be 0 or greater.  

- **auto_leave_after_min:**
If set to a value greater than zero, the bot leaves every meeting after the specified time (in minutes). Useful if you know the length of your meeting, if this is left a the default the bot will stay in the meeting until a new one is available. Default is the length of a class

- **headless:**
If true, runs Chrome in headless mode (does not open GUI window and runs in background).

- **mute_audio:**
If true, mutes all the sounds.

- **chrome_type:**
Valid options: `google-chrome`, `chromium`, `msedge`. By default, google chrome is used, but the script can also be used with Chromium or Microsoft Edge.

- **blacklist_meeting_re:**
If calendar meeting title matches a regular expression, it goes to blacklist.
Leave empty to attend to all meetings.
Default is "Cura|Free Period" to block cura and free period meetings


## Run the script

 1. Rename the [config.json.example](config.json.example) file to "config.json"
 2. Edit the "config.json" file to fit your preferences (optional)
 3. Install dependencies:   ```pip install -r requirements.txt```
 4. Run [auto_joiner.py](auto_joiner.py): `python auto_joiner.py`
