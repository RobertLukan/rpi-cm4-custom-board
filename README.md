Based on my previous projects I needed a customized RPI4 carrier board with 2 cameras input. The initial idea was taken from this project: https://www.tindie.com/products/dronecz/minimal-carrier-board-for-compute-module-4/.

I made several changes such as 4-layer PCB, added second camera lanes, differential routing for both cameras and HDMI, added temperature sensor, and added I2C and UART connectors.

I have added also two jumpers that allow disabling wireless and Bluetooth. I have tested nearly every connection. SD card connector does not work if you are using RPI4CM with emmc, otherwise, it should(not the fault of this design but the RPI design decision that I was not aware of while making this board)

In general, I am quite happy with the setup. JLCPCB manufactured and assembled most of the parts. However, one board did not have Hirose connectors soldered properly, I have received a coupon. I have not touched the spacing for Hirose connectors, but I found it may be slightly off. It is hard to connect RPI for the first time. But I don't want to modify it as it has been working for several weeks.

USB connector can be used(not only for flashing the CM), there is a dedicated jumper(OTG) for thir purpose. It is just USB2.0 and it is not delivering any power. I have tested powered USB hub/docking station and it is working fine. In this way even Ethernet connection can be used (again being limited to USB2.0)

I also created 3D-printed housing. It is my first 3d design of this type/scale, but it works. It does not have cutouts for HDMI and USB2.0 as I dont need them.

In order to use both cameras, config.txt file has to include both overlays as defined below, for my two cameras:

dtparam=i2c_arm=on

dtoverlay=imx708,cam0

dtoverlay=imx477,cam1

