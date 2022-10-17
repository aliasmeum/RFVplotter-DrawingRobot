# RFVplotter-DrawingRobot
Design files are up to date 17.10.2022 and can be found here.
Build description will be made available on www.robertfriberg.no

# Credits #
-   Thanks to [Herbert Roider](https://github.com/bertlr) for the original vplotter program, and for the excellent instructions on installation and use.
    I have only modified the program to include a hardware PWM-control for a BLDC-motor. This drone-motor and propeller is used for pushing the plotter head against the paper.

-   Thanks to Niklas Johansson and Lars Aurtande for the inspiration to make my own vplotter.

# Installation of the vplotter program #

- Install raspian: [www.raspberrypi.org/downloads/](https://www.raspberrypi.org/downloads/)

- Install necessary packages: git, cmake, flex and [wiringPi](http://wiringpi.com)

        sudo apt-get install git-core cmake flex wiringpi

- Download and build vplotter:

        git clone https://github.com/aliasmeum/RFVplotter-DrawingRobot.git
        cd RFVplotter-DrawingRobot-main\RFVplotterCode
        cmake .
        make
        sudo make install        

# Running the vplotter program #

The plotter needs some command line arguments:

- x0            :    Horizontal distance from center of the left stepper motor to the zero point on the canvas in mm.
- y0            :    Vertical distance from center of the left stepper motor to the zero point on the canvas in mm.
- baselength    :    The center distance between the stepper motors in mm.
- z_up          :    A value for the servo motor to lift the pen (1 - 100)
- z_down        :    A value for the servo motro to drop the pen (1 - 100)
- steps         :    Steps/mm for the plotter head. [Prusa calculator](https://blog.prusa3d.com/calculator_3416/)
- bldc_dutycycle: Dutycycle for the bldc motor (50-100). Set to 0 for running the plotter without the motor running.


Run the plotter as root:

    sudo vplotter --x0=557 --y0=660 --baselength=1114 --z_up=16 --z_down=20 --steps=80 --bldc_dutycycle=55

Run the plotter with a g-code file:

    sudo vplotter --x0=557 --y0=660 --baselength=1114 --z_up=16 --z_down=20 --steps=80 --bldc_dutycycle=55 < filename.ngc


Stop the plotter with <kbd>Ctrl</kbd>+<kbd>C</kbd>.

The Z-axis can lift or drop the pen. A value >0 lift the pen, and <=0 drop the pen.

    G0 Z0 (move the pen down)
    G0 Z1 (raise the pen up)