# SDCARDINSTALL
Gameboy Zero SD Card Install Instructions


///////////////////







Download the latest retropie image from here

https://retropie.org.uk/download/


It's the red button on the left. After downloading you need to turn what you just downloaded into an "image" To do this, you can extract it to an image file by right clicking then going to Extract, choose a file location and then the image should have a CD disc looking icon called 

retropie-4.4-rpi1_zero

It's version 4.4 as of this writing.

Then instead of just dropping and dragging the icon to your micro SD card location, you have to "write" the image to the micro SD card.  I recommend a program called Win32DiskImager, this you can use to put the extracted image on the SD card.  NOTE: Make sure you use the correct drive path, don't do what I did once and accidentally wipe a backup hard drive, just to be safe I'd unplug all connected USB storage devices just to be extra sure you put the image on the correct drive.

Then once the image file is on the micro SD card, pop it in the side of the Gameboy Zero and power it on, it should take 2-3 minutes for a first time boot up.  After a few minutes you will come to a gray screen reading "NO GAMEPAD DETECTED"

At this point you need to configure the controller by downloading a program called RetroGame directly to the Gameboy Zero, the easiest way to login to wifi is by using a usb keyboard to set up a temporary joystick.  I recommend using W, S, A, D for Up, Down, Left, Right. N, M for START, SELECT and J, K for A, B.  And that's all the buttons you need for now, after this hit J for the rest of the buttons and the Hotkey at the end and then hit J again (or whatever you selected for 'A') until you reach the RETROPIE main menu screen with the black top and bottom with white background.  

Now hit your selected 'A' button again and you should see a list of options, scroll down to WIFI and here it will be pretty self explainitory.  Login to your wifi, enter your password, and then it will bring you back to the main wifi screen, toggle right to select EXIT and then you should be logged on to wifi, or should be in a minute or so.  Now you can download Retrogame.  

*If you are comfortable logging into wifi directly through the command prompt, go ahead and hit F4 then do so.  Otherwise...



While in the main RetroPie menu, hit F4, this will bring you to the command prompt.  Type this in exactly and hit return at the end of each line,


cd
curl https://raw.githubusercontent.com/adafruit/Raspberry-Pi-Installer-Scripts/master/retrogame.sh >retrogame.sh
sudo bash retrogame.sh


The 'cd' makes sure you are in the correct position to search, the next line downloads the actual retrogame file, so here there will be some text with some numbers, the last 'sudo bash retrogame.sh' runs the file you just downloaded.  If it doesn't launch you into a new screen, repeat the steps until you see some numbers on the right, you just might not be fully logged onto wifi yet.

The next screen will be a list of options, you want to select 

"Six buttons + joystick"

Then select the option to restart and let it boot back up.

Now once it's booted up, for the last time (I promise) remove the SD card again and pop it back into your computer, at this point you only have 2 things to do.  Open up the file on your SD card titled 'retrogame.cfg' You can open it to almost any text editor, notepad should work, I like a program called Sublime Text2.  Once open in the text editor you should see these buttons mapped or listed like so,


LEFT      10  # Joypad left
RIGHT     22  # Joypad right
UP        23  # Joypad up
DOWN      27  # Joypad down
LEFTCTRL   4  # 'A' button
LEFTALT   25  # 'B' button
Z         11  # 'X' button
X          5  # 'Y' button
GND        6  # Spare ground point for 'Y' button
SPACE     16  # 'Select' button
ENTER     26  # 'Start' button
ESC    16 26  # Hold Start+Select to exit ROM

You only need to add the L and R buttons which are not listed here, do so by typing this below


A         12  #
S         13  #

So the button mapping looks like this


LEFT      10  # Joypad left
RIGHT     22  # Joypad right
UP        23  # Joypad up
DOWN      27  # Joypad down
LEFTCTRL   4  # 'A' button
LEFTALT   25  # 'B' button
Z         11  # 'X' button
X          5  # 'Y' button
GND        6  # Spare ground point for 'Y' button
SPACE     16  # 'Select' button
ENTER     26  # 'Start' button
ESC    16 26  # Hold Start+Select to exit ROM
A         12  #
S         13  #


Save this file and close it, then open up a file called config.txt, then add this line of code to the bottom


dtoverlay=pwm,pin=18,func=2


Then save and exit, this line of code turns on the audio output and puts it to pin 18, that is the pin in which the audio speaker is wired.  Then after that put the SD card back in the Gameboy Zero and turn it on, and with the USB keyboard, once at the main menu use the keyboard to hit your selected "START" button, then scroll down to CONFIGURE INPUT, after hitting A again you will be back to the request for button mapping and it again will say no GAMEPAD DETECTED.  That's because we just mapped the buttons directly to the Raspberry Pi.  Now you can remap the buttons using the available buttons on the Gameboy Zero.

Before adding any roms there are 2 more things I recommend, select AUDIO, then use the arrow keys on the USB keyboard to select number 4, audio mixer, this will take you to a master volume, use the arrow keys to put it up to 80 or 90 for more audile audio.  Then hit ESC to save.  And I recommend a font size increase, this can be done by typing F4, then

sudo nano /etc/emulationstation/themes/carbon/carbon.xml

Then enter and scroll down under "gamelist"  here change the fontsize for 0.030 to 0.050.  And again about a page down in another category called "gamelist"  Also change that from 0.03 to 0.05.  Then hit CTRL + X at the same time and it will ask you to save, hit Y then it should bring you back to the command prompt.  Type 'emulationstation' to get back to the main page. 

For the rom transferring I'll refer you to this link

https://github.com/retropie/retropie-setup/wiki/Transferring-Roms

THANK YOU AGAIN AND HAVE FUN!!


