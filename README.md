# RFVplotter-DrawingRobot
Design files are up to date 16.10.2022 and can be found here.
Build description will be made available on www.robertfriberg.no

Installation of vplotter

    install raspian: www.raspberrypi.org/downloads/

    install necessary packages: git, cmake, flex, wiringPi

      sudo apt-get install git-core cmake flex wiringpi

    download and build vplotter:

      git clone https://github.com/aliasmeum/RFVplotter-DrawingRobot.git
      cd vplotter
      cmake .
      make
      sudo make install        
