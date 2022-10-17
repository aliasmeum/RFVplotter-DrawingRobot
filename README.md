# RFVplotter-DrawingRobot
Design files are up to date 16.10.2022 and can be found here.
Build description will be made available on www.robertfriberg.no

# Installation of the vplotter program #

- install raspian: [www.raspberrypi.org/downloads/](https://www.raspberrypi.org/downloads/)

- install necessary packages: git, cmake, flex, [wiringPi](http://wiringpi.com)

        sudo apt-get install git-core cmake flex wiringpi

- download and build vplotter:

        git clone https://github.com/aliasmeum/RFVplotter-DrawingRobot.git
        cd RFVplotter-DrawingRobot-main\RFVplotterCode-v1
        cmake .
        make
        sudo make install        

# Running the vplotter program #

The plotter needs some commandline arguments:

- x0            :    Horizontal distance from center of the left stepper motor to the zero point of the canvas in mm.
- y0            :    Vertical distance from center of the left stepper motor to the zero point of the canvas in mm.
- baselength    :    The center distance between the stepper motors in mm.
- z_up          :    A value for the servo motor to lift the pen (1 - 100)
- z_down        :    A value for the servo motro to move down the pen (1 - 100)
- steps         :    Steps/mm for the plotter head.
- bldc_dutycycle: Dutycycle for the bldc motor (50-100). Set to 0 for running the plotter without the motor running.


Run the plotter as root:

    sudo vplotter --x0=500 --y0=650 --baselength=1000 --z_up=16 --z_down=20 --steps=80 --bldc_dutycycle=55

Run the plotter with a g-code file:

    sudo vplotter --x0=500 --y0=650 --baselength=1000 --z_up=16 --z_down=20 --steps=80 --bldc_dutycycle=55 < filename.ngc


Stop the plotter type <kbd>Ctrl</kbd>+<kbd>C</kbd>.

The Z-axis can lift or drop the pen. A value >0 lift the pen, and <=0 drop the pen.

    G0 Z0 (move the pen down)
    G0 Z1 (raise the pen up)