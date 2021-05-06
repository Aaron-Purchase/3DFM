# 3DFM
Automated 3D magnetic flux density mapping system

#Software and hardware
- Ubuntu 20
- Python 3.9
- Arduino UNO: https://store.arduino.cc/usa/arduino-uno-rev3
- Arduino gShield: https://synthetos.com/project/grblshield
- Any 3D CNC/3D printer arm (see picture in 3DFM/Photo/)
- USB Hall-probe (Metrolab THM1176 used here). 

#Installation
1. Install single trigger code for the THM1176 probe (https://github.com/Hyperfine/pyTHM1176/tree/cedh/single_trig/)
	- place all 'pyTHM1176' subdirectory files into the 3DFM folder.
	
2. Flash GRBL 1.1h (i.e. the *.hex file) to the Arduino UNO.
	- see https://github.com/gnea/grbl/releases/
	- use HexUploader (https://github.com/paulkaplan/HexUploader) or similar
	
3. Change '/dev/ttyACM0/' of the 1DFM.py and 3DFM.py code to match your Arduino UNO port.
	- most often it is the same

4. Power ON the Arduino + gShield using a 24 V power supply unit
	- connect probe USB
	- connect CNC USB

5. Run 1DFM.py (projection) or 3DFM.py (volume).

#Notes
- recommend running 1DFM.py at first to test function.
- this is a very simple code to understand & reconfigure.
- must calibrate the steps for your machine (for example, x_forwords = 'G91 X-0.17 F100000') 
- other detailed calibrations can be done by modifying the .hex file through Arduino IDE.
- 3DFM will map in a zig-zag pattern over a defined volume.
- current default mapping range is 13.5 cm x 13.5 cm x 1 cm in steps of 3 mm x 3 mm x 1 mm.
- this code can be modified for measurement using any other USB probe (for example, RF fields, temperature, etc)

#Various useful code
- 'rewind.py' to be used to bring gantry head back to starting point (no measurements).

#Future work
- GUI
- various functions (homing, etc)
- circular 3D filling, other motion
- Bx, By, Bz, temperature data storage
- 3D visuals of mapping region and field plotting during process
