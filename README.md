Klipper config files for KP3s V2 (red extruder) and V3 (titan extruder)

NOTE: Robin_nano.bin file is compiled for F103 Processor. Usually found on the V2 with red extruder
If you need a .bin file for another processor, compile one using the "Build Klipper firmware for Kingroon KP3S" section of this guide: https://3dprintbeginner.com/how-to-install-klipper-on-kingroon-kp3s/

To know what processor you have, unscrew the bottom plate of the printer to get access to the mainboard.
Now just read what the MCU has written on it. Ex. STM32F103


Steps for Klipper installation:
1) Place Robin_nano.bin in the root of a microSD card and place in printer
2) Turn printer on and give it 60 seconds to update. Screen will go blank, it is normal
3) Turn printer off
4) Install mainsailOS or FluiddPI on raspberrypi of choice (cant go wrong with either, although I prefer Fluidd since you can change settings when printer is off)
5) Here is a great guide for mainsailOS https://3dprintbeginner.com/how-to-install-mainsailos-on-raspberry-pi/
6) And here is one for FluiddPI https://docs.fluidd.xyz/installation/fluiddpi
7) Turn on printer and connect the Pi to the USB port of the printer
8) Update all packages after acessing the GUI by typing the IP address of the pi into your browser
9) Read printer.cfg and uncomment/update sections that need to be uncommented or updated
10) Place/update printer.cfg in the confugration section where moonraker.cfg exists 
11) Click restart firmware on the main page
12) Calibrate esteps https://youtu.be/T-knWbh1Gg8?t=551. Extrude filament with the nozzle at printing temperature. Do not cold extrude like in the video. Just follow his calculations 
13) Only do steps 14 and 15 if you have bltouch
14) Home all axis, and in console run "probe_caliberate". Place a piece of paper under the nozzle and adjust the Z until there is slight friction when you move the paper. Save, restart
15) Home all axis, and do a bedmesh (in Fluidd, go into tools tab and hit calibrate, after its done, save, restart firmware)
16) Do step 17-18 if you do not have bltouch
17) type "bed_adjust_screws" in console
18) Place a piece of paper under the nozzle and adjust the bed screws until there is slight friction when you move the paper. Save, restart
19) Lastly, do a pid calibrate for bed and extruder:
20) PID_CALIBRATE HEATER=extruder TARGET=210  wait about 5 minutes then save and restart
21) PID_CALIBRATE HEATER=heater_bed TARGET=60 wait about 10 minutes then save and restart
22) All done! Happy printing
