# Anarchist Library Belt

*A fork of Astrrra's [Anarcho Earrings](https://github.com/Astrrra/AnarchoEarrings) as requested by MNHarold*

Hi all, as promised here's a little easy guide on how to make your own portable WiFi anarchist libary. I will try to make it as easy and accessible as possible - if anything is unclear feel free to reach out to me on [reddit](https://www.reddit.com/user/aruffj_).

This guide aims to leave you with a fully working Anarcho Library Belt, however it does not try to teach you programming. 

What we need:
* An ESP8266 or ESP32 Microcontroller
* A Micro-USB Cable
* A PC (Linux/Win/Mac) - A raspberry pi would do. 
* The Arduino IDE
* Some electrical tape
* A USB Powerbank

**Note**: You can simply search for the ESP32/ESP8266 online and buy them. The ESPs are a so called "Micro Controller" which allows you to programm it. You should be able to get one cheap (Less then 5€) new, I however recommend you also check your local "used stuff" site. :)

## Step 1: Setting up

Alright - let's go!

1. Take your ESP and connect it to your PC with an USB cable. There should be an LED lighting up indicating that it's connected.
1. Now we have to download the Arduino IDE (Integrated Development Envoirement) to connect to the micro controller and send it the required data. You can download it for free from [here](https://www.arduino.cc/en/software). If you are using Linux you will want to use your package manager instead of the website.
1. Install the IDE as usual (Windows: Double click the .exe file you downloaded, Mac: Unpack the .zip file to software)
1. Start the IDE. We will have to add some settings. :)
1. Click on `File` -> `Preferences`. In the lower part of the new window you will find `Additional Boards Manager URLs:` -- Copy and paste this: `http://arduino.esp8266.com/stable/package_esp8266com_index.json` (This will allow us to communicate with our Board. :) ) Press "Ok".
![Arduino IDE Preferences Dialoge](/pictures/01_arduino_preference_dialoge.png)
1. In the main window go to `Tools -> Board -> Board Manager`. Search for `esp8266` and click on `Install`. This might take a second depending on your internet speed. :) Close the website then.
![Arduino IDE Board Manager Dialoge](/pictures/02_arduino_board_manager_dialoge.png)
1. In the main window again go to `Tools -> Boards: -> ESP8266 Boards (3.0.2)`. Select your board from the list - if in doubt use `Generic ESP8266 Module` 
1. Now close the IDE again - we have to do some additional work before we continue there.
1. Visit the [LittleFS](https://github.com/earlephilhower/arduino-esp8266littlefs-plugin/releases) release page and dwonload the `ESP8266LittleFS-2.6.0.zip`. This will allow us to upload the actual Anarchist FAQ to the Board.
1. Open the Zip-File and extract the contents to
    * Linux: `~/Arduino/tools/`
	* Windows: `C:\Program Files (x86)\Arduino\tools` (Your PC might ask you if you really want to here, say "Yes")
	* Mac: Create the `tools` folder in `~/Documents/Arduino` and unpack the files there
1. Now download the arduino project from [here](https://github.com/aruffj/AnachoLibraryBelt/releases/tag/v1.0) and unzip it wherever you like.
1. Open the File `AnarchoFAQ.ino` from the unzipped folder. This should open the Arduino IDE again.
1. Directly under the menu you will find an arrow icon. Click it and it should upload the program to the micro controller. If this doesn't work look at the Troubleshooting section at the end of the guide. You will see a status update in the lower black window. It will tell you there when it's finished. :)

![Arduino IDE Compile and Upload](/pictures/03_arduino_compile_and_upload.png)
1. When your compile and upload succeeded reconnect the ESP Board (if in doubt: Unplug the cable and plug it in again; some boards have a `RST` (Reset) button directly on the board which can also be used.
1. Now go to `Tools -> ESP8266 LittleFS Data Upload`. This takes a minute or two - go and get yourself some water!
1. The ESP itself is now prepared. Next step: Handy work!

## Troubleshooting
*Issue: Arduino IDE can't find my board!* 

*Solution:* Make sure you have the right COM Port selected. If you are unsure which one is the correct one make sure to not connect any USB Stuff besides your ESP and Mouse/Keyboard for the process.

*Issue: Arduino IDE can't find my board under Linux!*

*Solution:* Run the IDE with `sudo`. Depending on your settings your current user might not be able to mount USB devices which can cause the issue. You will have to replicate `Step 1` again and copy the `ESP8266LittleFS-2.6.0.zip` to `/root/Arduino/` instead. **NOTE**: This is a quick way to do this and absolutely not recommended. Please check for your distro on how to get the correct permissions to your user account. 