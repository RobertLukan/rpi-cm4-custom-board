Based on my previous projects I needed a customized RPI4 carrier board with 2 cameras input. The initial idea was taken from this project: https://www.tindie.com/products/dronecz/minimal-carrier-board-for-compute-module-4/.

I made several changes such as 4-layer PCB, added second camera lanes, differential routing for both cameras and HDMI, added temperature sensor, and added I2C and UART connectors.

I have added also two jumpers that allow disabling wireless and Bluetooth. I have tested nearly every connection. SD card connector does not work if you are using RPI4CM with emmc, otherwise, it should(not the fault of this design but the RPI design decision that I was not aware of while making this board)

In general, I am quite happy with the setup. JLCPCB manufactured and assembled most of the parts. However, one board did not have Hirose connectors soldered properly, I have received a coupon. I have not touched the spacing for Hirose connectors, but I found it may be slightly off. It is hard to connect RPI for the first time. But I don't want to modify it as it has been working for several weeks.

USB connector can be used to connect external devices. To flash a CM the dedicated jumper(OTG) needs to be connected . It is just USB2.0 and it is not delivering any power. I have tested powered USB hub/docking station and it is working fine. In this way even Ethernet connection can be used (again being limited to USB2.0)

I also created 3D-printed housing. It is my first 3d design of this type/scale, but it works. It does not have cutouts for HDMI and USB2.0 as I dont need them.

In order to use both cameras, config.txt file has to include both overlays as defined below, for my two cameras:

dtparam=i2c_arm=on

dtoverlay=imx708,cam0

dtoverlay=imx477,cam1

The majority of the connectors were assembled by JLCPCB(without I2C and camera connectors - not available at that time), I have included the production directory where all the details are attached. The positions of parts are not 100% aligned, so make sure if you are asking JLCPCB to assemble parts to align them correctly. It is very important to order the correct camera connector: https://www.digikey.at/en/products/detail/amphenol-cs-fci/SFW15R-1STAE1LF/4270877

I made several design decisions that suited my needs, such as different GPIO header connector, and 4-pin Groove connectors for UART and I2C, so they might not be suitable for your needs.

One important detail, I am powering this board with the Raspberry Pi power supply. Other power supplies with USB C connector might not work as RPI requires quite some power and I would need to implement USB PD.

Update:
I needed power(5V) for an external USB device. I knew that I could connect a powered USB docking station(hub), however, that requires yet another power supply. As I just needed to power the USB microphone, that was an overkill. I looked at my diagram and I noticed that I can take 5V from GPIO and connect one of the pins at the OTG jumper(as shown below). An important detail is that the track is not designed to carry a lot of current, so be reasonable. 

<img width="615" alt="Screenshot 2024-01-21 at 12 54 01" src="https://github.com/RobertLukan/rpi-cm4-custom-board/assets/15019985/78a3a4ae-f855-410a-9d0c-685198d1b0c8">


License:
Please feel free to use the design. Released under the following license: 
https://ohwr.org/cern_ohl_p_v2.txt

