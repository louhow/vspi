## About VSPi ##

VSPi is an education server targeting developing countries. The hardware is based on Raspberry Pi computers because they are inexpensive and efficient. The server software runs on nginx and runs WordPress because there is an large community of developer support. [Read more about VSPi on the Village Science site.](http://villagescience.org/vs-pi/) 

No matter your level of experience, your contributions to the project are welcome. The steps for installing the VSPi code are listed below, give it a try and let us know what you think.

## Hardware Configuration ##

* Raspberry Pi - Model B (512 MB / Revision 2)
* Edimax 150 Mbps Wireless 11n Nano Size USB Adapter
* Transcend 32 GB Flash Memory Card
* Raspberry Pi Case
* Micro USB power plug

## Installing `vspi` ##

Download the latest NOOBS from [raspberrypi.org/downloads](http://www.raspberrypi.org/downloads). NOOBS Lite (network install only) will be a smaller download since it doesn't grab the OSes until you pick one at install but if you plan to reinstall Raspbian several times, it'll have to re-download the OS each time.

Follow the instructions from the [Quick Start Guide [PDF]](http://www.raspberrypi.org/wp-content/uploads/2012/04/quick-start-guide-v2_1.pdf) to install Raspbian using NOOBS.

Once Raspbian is installed, your Pi will reboot and then go in to a blue and red config window. We don't need to do anything here so hit 'Finish' and you should be taken to the command prompt.

Run this command to install and configure VS-Pi:

    git clone https://github.com/villagescience/vspi.git && sudo bash ./vspi/setup.sh

The setup script will now run and might take over 10 minutes depending on your connection. The script sets up and configures:

* **WordPress**: website content platform.
* **nginx**: webserver for wordpress.
* **PHP/MySQL**: backend for wordpress.
* **Redis**: page cache for wordpress to reduce page loading times.
* **hostapd**: wireless access point daemon to make the vspi act as a wireless hotspot.
* **iptables**: forwards requests to the outside internet from wireless clients
  to the raspberry pi's ethernet port, i.e. makes the vspi act as a wireless router.
* **dnsmasq**: DNS/DHCP server to allow wireless clients to lease IP addresses and
  resolve internal pages under the `*.vspi` domain.

After the script finishes, your Pi will reboot. Once it's booted back up, you can join the wireless network "VS-Pi Connect" and navigate to http://vspi . You should see the wordpress-based homepage.

If your Raspberry Pi is connected to the internet through its ethernet port, you should also be able to browse to the outside internet while connected to "VS-Pi Connect".

### WordPress ###

Also see [villagescience/wordpress](https://github.com/villagescience/wordpress) for the repo of our base WordPress install that's packaged with VSPi.
