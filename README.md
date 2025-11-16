# Bruce-20-seconds-RF-ByPass
This repo explains how to install a custom firmware to bypass the 20-second limit of the ITMT and FULL jammer in RF.
For now, there's only the version for the LilyGo T-Embed CC1101; the other versions for the M5, etc., will come later.

1- You need to have Python installed; to do this, you need to go to the official Python website and download it for Windows.
  Don't forget to click "add to path" on the installation screen !
  To check if you have Python installed, you can open a command prompt and type `python --version`

2- We're now going to install a Python utility called "esptool", which is a tool for flashing the device with a .bin firmware file.
  Open a command prompt as administrator and type: `python -m pip install esptool`
  To check that esptool is properly installed, you can type: `esptool version`

3- You now need to connect your device to your PC and put it into flash mode. Here are all the methods depending on your device :
  - Cardputer: Turn off and unplug from USB, hold the btn G0 (upper right corner), then connect via USB.
  - StickCs: Turn off, connect one side of a jumper cable into GND and the other side in G0, plug in USB, then remove the jumper cable.
  - T-Embed: Keep encoder center button pressed and press RST button (CC1101 this btn is on the board, beside ESP32-S3 chip).
  - T-Deck: Keep the trackpad button pressed and press RST (in the left side).
(You can also watch tutorials on YouTube if you're having trouble.)

4- Once your device is connected in flash mode, we will identify its COM number in order to flash it with esptool. To do this, follow these steps :
  Go to your Windows search bar and type "Device Manager". Once in the window, scroll to the bottom and expand the "Ports (COM & LTP)" tab. If you see two COM ports, for example: COM1, COM3, your device is correctly connected!
  You must therefore note the COM port of your device; discard COM1, as it's the Windows port. Most often, it's COM3.

5- You can now download the .bin file located in the released GitHub repository.

6- Once you have the COM port that belongs to your device and the .bin file, we can flash it with esptool. To do this, follow these steps :
  Go to your downloads folder and right-click on the .bin file, then select Properties. Copy the file's location, for example: C:\Users\exemple\Downloads
  Open a command prompt as administrator and paste what you copied earlier and add `cd` before, for example : `cd C:\Users\exemple\Downloads`
  Once you are in the directory containing the .bin file, you must now enter the following : `python -m esptool --chip esp32s3 --port COM3 write_flash -z 0x0 "the name of the .bin file"`
  (Replace `COM3` with the COM number of your device if it is different.)
  (Between the "quotation marks" you must indicate the name of the .bin file, exemple : "Bruce-lilygo-t-embed-cc1101.bin"

  The flash should normally start; do not unplug your device, keep it firmly in place without touching it until it finishes.
  Once you see the message: "Hard resetting via RTS pin..." you can unplug your device, turn it on and the firmware should be flashed correctly.

So on this .bin file I removed the 20-second limit and put a 99999999999 second limit in its place.

IMPORTANT ! If you have any problems, you can contact me on Discord: `mokapi47` via private message so I can help you.
