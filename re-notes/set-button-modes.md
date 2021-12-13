Apparently pressing the set button 1x puts the RF remote in to 'learn/pair' mode: 
https://www.youtube.com/watch?v=B4tDQiwhBWc&t=2m8s


I posted some payloads after pushing the button several times in a row:

https://github.com/arendst/Tasmota/issues/7385#issuecomment-991848762



Looking at the payloads minus the common segment (`55AA030700106500000C48000007`)

01 02 03 04 05 06 07 08 CK
--------------------------------------
02 3E 00 64 00 01 01 F5 74
02 3E 00 64 00 02 02 F7 78
02 3E 00 64 00 03 03 F9 7C
02 3E 00 64 00 04 04 FB 80
02 3E 00 64 00 05 05 FD 84

00 00 00 00 00 01 01 51 2C
00 00 00 00 00 02 02 53 30
00 00 00 00 00 04 04 57 38
00 00 00 00 00 05 05 59 3C

01 3A 00 64 00 01 01 F0 6A
01 3A 00 64 00 02 02 F2 6E
01 3A 00 64 00 03 03 F4 72
01 3A 00 64 00 04 04 F6 76
01 3A 00 64 00 05 05 F8 7A


Very confident that `06` and or `07` is the 'mode` or number of times that the button has been pushed.
The color of the LEDs DOES change with each button press so the other changed bytes _could_ be the color/saturation/brightness values. Not sure. 

The second group of payloads is from the controller after it had been powered up but not been given any commands (other than the periodic tasmota heart beat). 
It looks like mode `03` is unlocked only after sending a color command. 

Before any color command is set, button pressing just skips over this mode?
