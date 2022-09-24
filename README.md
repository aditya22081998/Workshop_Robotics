#Konfigurasi Framework HROS-1

##AutoLogin User Ubuntu

sudo gedit /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf

autologin-user= $username  

##Instalasi Remote Desktop Server

https://skjoldtech.wordpress.com/2020/02/28/how-to-install-x11vnc-server-on-linux-mint-19-with-autostart-on-boot/

##Instalasi Environtment

sudo usermod -a -G dialout $USER

sudo reboot

sudo apt-get update

sudo apt install openssh-server

sudo apt install apache2

sudo apt install make

sudo apt-get install g++ manpages-dev libjpeg62-dev libncurses5-dev git


##Clone Framework Darwin Op

https://github.com/darwinop-ens/darwin-op

##Clone Framework HROS1

https://github.com/Interbotix/HROS1-Framework

--- Program change

step 1. change camera.h
change

	static const double VIEW_V_ANGLE = 46.0; //degree
	static const double VIEW_H_ANGLE = 58.0; //degree

to

	static constexpr double VIEW_V_ANGLE = 46.0; //degree
	static constexpr double VIEW_H_ANGLE = 58.0; //degree

step 2. clean

    go to directory Linux/build
    make clean

step 3. add library unistd

    go to Framework/include/motionManager.h
    add #include <unistd.h>
    go to Linux/project/demo/VisionMode.cpp
    add #include <unistd.h>

step 4. add library stat

    go to Linux/include/LinuxCamera.h
    add #include <sys/stat.h>

step 5. build

    go to directory Linux/build
    make all

step 6. pthread

    open Makefile in demo

    change

    LFLAGS += -lpthread -ljpeg -lrt

    to

    LFLAGS += -pthread -ljpeg -lrt

step 7. flag

    move $(LFLAGS) to end

 

