# Installations

## VSCode (January 2026)

To download VSCode on your Jetson, watch this very helpful YouTube Video

https://www.youtube.com/watch?v=epSAtsCOii4

The steps that were done in this video were

1. Open Terminal
2. run `sudo apt update`
    - enter password
    - `clear`
3. run `sudo apt upgrade`
    - answer `Y` 
    - you'll get a notification saying you need to reboot, **important** do NOT reboot yet!
    - `clear`
4. run `sudo apt install python3-pip`
    - enter password
    - answer `Y`
    - `clear`
5. run `sudo pip3 install -U jetson-stats`
6. reboot!!!
7. run `jtop`
    - check the model name! 
8. start webbrowser (preferably firefox)
9. search for **vs code 1.85.2**
    - choose the latest version after pressing on the first link which will say something like: **november 2023 (version 1.85)**
10. You're going to want to choose X.Y.2 or whatever is the latest.
11. Click on the linux *Arm* link.
12. Search for **Linux Arm64 debian** copy the link, which can be something like:
- *https://update.code.visualstudio.com/{version}/linux-debarm-64/stable*
13. Open terminal
14. cd to Downloads by running `cd ~/Downloads/`
15. run `wget` + link 
    - https://update.code.visualstudio.com/{version}/linux-debarm-64/stable
    - **BUT** replace */{version}/* with the version you'd like to use
    - which can be */1.108.2/*
16. run `ls`, this will tell you the name.
17. run `sudo dpkg -i stable` in your terminal. 
18. Now that we have installed VSCode, you can start it up by running `code` in your terminal. **OR** you can search Visual Studio Code in activities.

EXTRA's

Now that you've downloaded it
- download the *python* extension.
- now you can open a folder. 
