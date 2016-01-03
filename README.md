# esp8266-vagrant

Vagrant project for setting up esp8266 toolchain.

## How to install

Run on the host OS:

	vagrant up
	vagrant ssh

Run inside the vagrant VM:
	
	cd esp-open-sdk
	make STANDALONE=y
	echo "PATH=$(pwd)/xtensa-lx106-elf/bin:\$PATH" >> ~/.profile

Exit and re-enter the VM to reload ~/.profile:

	exit
	vagrant ssh


## Usage

SDK is located under:

	/home/vagrant/esp-open-sdk/esp_iot_sdk_v1.4.0

Bin directory (gcc, ld, gdb, etc.) is located under:

	/home/vagrant/esp-open-sdk/xtensa-lx106-elf/bin

Root of this project in mounted under /vagrant in VM.


## Flashing

I recommend using esptool from host OS, so that you don't have to switch serial port converter from VBox to host OS and back, when switching between programming and watching serial I/O.

Example command:

	~/Projects/esptool/esptool.py -p /dev/tty.SLAB_USBtoUART write_flash 0x00000 firmware/0x00000.bin 0x40000 firmware/0x40000.bin


## Examples

Examples can be found at https://github.com/esp8266/source-code-examples. Please note that you need to change SDK and bin/ path to ones specified above.


## Resources

* https://github.com/adafruit/esp8266-micropython-vagrant
* https://github.com/pfalcon/esp-open-sdk
