# rbpi-i2s-devicetreeoverlay
Most (all?) versions of the Raspberry Pi have an I2S digital audio interface. This is however not possible to enable easily by raspi-config or similar tools. Instead one has to make a "Device Tree Overlay" file. The dts file in this repo should be compiled with 

dtc -@ -I dts -O dtb -o rbpi-i2s.dtbo rbpi-i2s.dts

The file rbpi-i2s.dtbo must then be copied into /boot/overlays and in the file /boot/config.txt a line with

dtoverlay=rbpi-i2s

shall be added. Also there should (probably) be a line, not commented out, like this

dtparam=i2s=on

and, if desirable, the PWM-audio interface can be disabled by commenting out like this

#dtparam=audio=on

After reboot, the i2s-interface should be visible when typing "aplay -l" or "aplay -L".

--

Good link: https://www.raspberrypi.com/documentation/computers/configuration.html#device-trees-overlays-and-parameters
