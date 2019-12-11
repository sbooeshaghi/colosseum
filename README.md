# colosseum: open source fraction collector

<p>A modular, highly customizable, open source fraction collector.</p>

![The colosseum fraction collector](HARDWARE/colosseum_homeview.png)

## Tl;dr
We present colosseum, a low-cost, modular, and automated fluid sampling device for scalable microfluidic applications. The colosseum fraction collector can be built for less than $100 using off-the-shelf components, and can be assembled in less than an hour. It uses 3D printed parts and common components that can be easily purchased from many retailers. The device can be run from a Windows, Mac, Linux, or Raspberry Pi computer with an easy-to-use GUI.

## What's included?
<ul>
  <li>Computer Aided Design (CAD) files of the 3D printed components.</li>
  <li>Controller software (Python) and a graphical user interface (GUI) to control the pumps.</li>
  <li>Arduino firmware to send commands to the motors and receive commands from the GUI.</li>
  <li>Bill of materials for sourcing and purchasing materials.</li>
  <li>Detailed assembly instructions of hardware components.</li>
  <li>Single click executable files for Mac, Windows, Linux, and Raspberry Pi systems.</li>
</ul>

## Getting Started
__What do I need to buy?__
The bill of materials with prices and vendor links is available on a [Google Spreadsheet](https://docs.google.com/spreadsheets/d/1Z83jh0TSUGW6AqqXLzAsNthaGQMtfY0oZQ2VZEOLgi0/edit?usp=sharing).

__What do I need to make?__
The 3D printed components can be fabricated on any desktop fused filament fabrication (FFF) 3D printer. They were designed using Autodesk Fusion 360, a proprietary CAD software that offers free academic licenses. STL, STEP, IGES, Fusion 360 archive files, and bill of materials are available in the HARDWARE/ folder.They can be used with any slicing software to generate GCode for 3D printing.

_Build Videos (Coming soon)_

### Setting up the Arduino
We use the Arduino CNC shield to allow for up to three fraction collectors to be controlled from a computer.

The software is configured to run the stepper motors with 200 steps per revolution at 1/4 microstepping, which translates to 800 steps per rotation. To configure this, it is necessary to add a jumper between the M1 pin of the Arduino CNC shield. More information about microstepping can be found in the product page for the DRV8825 Stepper Motor Driver, which is used by the [CNC shield](http://www.zyltech.com/arduino-cnc-shield-instructions/). 

The Arduino should be flashed with the arduino_serialCOM_v0.1.ino sketch, available in the SOFTWARE/ folder. (*)

Make sure to download and install the [AccelStepper library](http://www.airspayce.com/mikem/arduino/AccelStepper/classAccelStepper.html). To install, unzip the zip file to the libraries sub-folder of your sketchbook, if you get stuck here is a how-to.

The fraction collector is driven by an Arduino board that interprets commands sent via USB and sends the signals to control the stepper motor movement. For directions on how to flash an arduino please refer to the official guide: https://www.arduino.cc/en/Guide/HomePage

### Installing software
The Python scripts are available in the SOFTWARE/ folder. The GUI was created using Qt designer, a drag and drop application for organizing buttons that allows the used to easily make modifications. This GUI is used to interface with a Python script that controls both the microscope and Arduino via USB.

![Screenshot of the GUI](SOFTWARE/fc_ui.PNG)

The software you will need to run on your computer in order to control the Arduino is the colosseum_main.py script located in the SOFTWARE/ folder. To start up the UI, open up the terminal inside the folder with all of the .py and .ui files, and type:

python run.py

Before you run the system, MAKE SURE YOU HAVE INSTALLED THE ARDUINO FIRMWARE!!

## Startup Checklist
Before starting the Python controller, make sure
<ul>
  <li> The Arduino has the firmware uploaded to it
  <li> The Arduino is connected via USB to the computer
  <li> You have appropriately placed jumpers on the CNC Shield to allow for microstepping and hardware enabling (discussed in build video).
  <li> The CNC shield is powered, and that all motors are plugged in to the CNC shield
</ul>

## Running the software and testing the fraction collector
There are two ways to run the controller. The easiest way is to just double click the executable available below. Simply download the executable, double click it, and begin using it. Navigate to the Releases tab at the top to find the following executables.
<ul>
  <li> Windows
  <li> Mac OS
  <li> Ubuntu (coming soon)
  <li> Raspbian
</ul>

## Tips/Hints
Things that we have learned along the way that may help with your build.

Set the current limit on your motor controller to vary the stall torque. Increasing the current to the motor increases the stall torque and increases the max pressure that your syringe pump can run at. How to set the current limit.
