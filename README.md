# Teams-Auto-Joiner

Modified to work with Bellarmine College Preparatory meetings only.

- [Prerequisites](#prerequisites)
- [Configuration options](#configuration-options)
- [Run the script](#run-the-script)

Python script to automatically join Microsoft Teams meetings.
Automatically turns off your microphone and camera before joining. Automatic login and blacklist can be set in the config file.

Always joins the newest meeting and leaves either after a specified time, if you are the last person in the meeting or only if a new one is available (see [Configuration options](#configuration-options) for more information).
I also made a short tutorial video on how to setup the bot: https://youtu.be/YgkSOqfIjf4


## Prerequisites  
  
 - Python3 ([Download](https://www.python.org/downloads/))  
   
## New Config options  

- **check_interval:**  
Delay in seconds between checks for new meetings and participants  

- **join_early_offset:**  
Seconds early that the program will join the meeting. say class starts at 12:20, set at 60 seconds, it will join at 12:19.  

## Configuration options  
  
- **email/password:**  
The email/password of your Microsoft account (can be left empty if you don't want to automatically login)  

- **run_at_time:**  
Time to start the script at. Input is a string of the hour and minute in 24h format, if you want it to start immediately leave this empty. 
If a time before the current time is given, the next day is used. Also make sure that you entered your email and password.
For example, if you want the script to start searching meetings at 6 in the morning on the next day, you would input `06:00` in the config.

idk dont touch this one

- **meeting_mode:**
Since BCP only uses calendar meetings, none of the other modes are supported.
`3` Only calendar meetings  

- **organisation_num:**
1. No need to change.

- **random_delay:**
If true, adds a random delay (10s-30s) before joining a meeting. Can be useful so the bot seems more "human like".
Not very applicable since it does not really matter.

- **check_interval:**
The amount of seconds to wait before checking for meetings again. Only integer numbers greater than 1 are allowed.

- **auto_leave_after_min:**
If set to a value greater than zero, the bot leaves every meeting after the specified time (in minutes). Useful if you know the length of your meeting, if this is left a the default the bot will stay in the meeting until a new one is available.

- **leave_if_last:**
If true, leaves the meeting if you are the last person in it.

- **headless:**
If true, runs Chrome in headless mode (does not open GUI window and runs in background).

- **mute_audio:**
If true, mutes all the sounds.

- **chrome_type:**
Valid options: `google-chrome`, `chromium`, `msedge`. By default, google chrome is used, but the script can also be used with Chromium or Microsoft Edge.

- **blacklist:**
No longer needed since it only searches calendar meetings, while this blacklist affects channel meetings.

- **blacklist_meeting_re:**
If calendar meeting title matches a regular expression, it goes to blacklist.
Leave empty to attend to all meetings.
Default is "Cura|Free Period" to block cura and free period meetings


## Run the script

 1. Rename the [config.json.example](config.json.example) file to "config.json"
 2. Edit the "config.json" file to fit your preferences (optional)
 3. Install dependencies:   ```pip install -r requirements.txt```
 4. Run [auto_joiner.py](auto_joiner.py): `python auto_joiner.py`
