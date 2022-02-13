# DFD312
Firmware for the eStim MK312BT hardware
The MK312 project has delivered a nicely documented and complete hardware desctiption for building a eStim device inspired by the famous ET312. Firmware in binary format exists and works. This allows the community to build such devices. Great work. I did miss however possibility to change the firmware, extend and modify it. I could not find anything on the Internet about this so I dicided to write it on my own. This repository contains all files needed to compile the firmware and load it to a MK312-BT hardware. It works with the Arduino IDE and is simply structured. Functionality is beeing increased over time. At the time of the first release the basic functionality of the MK312 firmware is implemented. 
- Complete menu user interface identical to MK312
- Basic stimmulation pattern (wave, stroke ..)

Missing so far is:
- Audio patterns
- remote link / blue tooth
- Phase patterns
- Self test during startup

To generate the patterns, hardware -and software timers are used. The basic pulse that is generated by switinch on -and off the gates of the respective MOS FETs is quite short. Measuring the puls of the original MK312 shows me durations in the range of 5us - 130us. To achieve this is the 8MHz ATMega16, I use the hardware timers T2 and T3 for generating the pulses of both channels. Other variations of the output signal are slower so that a software timer works. Besides, the number of HW timers is limited to two (T1 is generally used by the Arduino SW).  The setup with these timers works. However, some optimization might be needed. The original MK312 generates pulses as fast as 3us. In my current setup I only reach 7us. Faster is possible but it seems that overall output signals get a bit of a jitter. Not sure if that is noticable when connecting the electrodes to  the body. Output signal strength is calibrated to the original device. This output level is generated via the DAC LTC 1661. Obviously, having access to the source code this can easily be changed. Thats one of th
