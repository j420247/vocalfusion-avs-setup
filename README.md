# xCORE VocalFusion 4-Mic Kit for AVS and Amazon Alexa Voice Services SDK on a Raspberry Pi

The XMOS **xCORE VocalFusion 4-Mic Kit for AVS** provides far-field voice capture using the XMOS XVF3000 voice processor.

Combined with a Raspberry Pi running the Amazon Alexa Voice Service (AVS) Software Development Kit (SDK), this kit allows you to quickly prototype and evaluate talking with Alexa.

To find out more, visit: https://xmos.com/vocalfusion-avs  
and: https://developer.amazon.com/alexa-voice-service

This repository provides a simple-to-use automated script to install the Amazon AVS SDK on a Raspberry Pi and configure the Raspberry Pi to use the **xCORE VocalFusion 4-Mic Kit for AVS** for audio.

## Prerequisites
You will need:

- **xCORE VocalFusion 4-Mic Kit for Amazon AVS**: XK-VF3000-L33-AVS
- Raspberry Pi 3
- Micro-USB power supply (min. 2A)
- MicroSD card (min. 16GB)
- Powered mono speaker with audio 3.5mm analogue plug
- Monitor with HDMI input
- HDMI cable
- Fast-Ethernet connection with internet connectivity

You will also need an Amazon Developer account: https://developer.amazon.com

## Hardware setup
Setup your hardware by following the **Hardware Setup** at: https://xmos.com/vocalfusion-avs

## AVS SDK installation and Raspberry Pi audio setup
Full instructions to install the AVS SDK on to a Raspberry Pi and configure the audio to use the **xCORE VocalFusion 4-Mic Kit for AVS** are detailed in the **Getting Started Guide** available from: https://xmos.com/vocalfusion-avs.

Brief instructions and additional notes are below:

1. Install Raspbian (Stretch) on the Raspberry Pi.

2. Ensure running kernel version matches headers kernel headers package. A typical system requires the following `--reinstall` command:

   ```sudo apt-get install --reinstall raspberrypi-bootloader raspberrypi-kernel```

   followed by a reboot.

3. Open a terminal on the Raspberry Pi and clone this repository:  
`cd ~; git clone https://github.com/xmos/vocalfusion-avs-setup`

4. Create a new Alexa device by following: https://github.com/alexa/alexa-avs-sample-app/wiki/Create-Security-Profile  
(Note: the *Allowed Origins* and *Allowed Return URLs* should use **http**, not https.)  

5. Run the installation script: `source ~/vocalfusion-avs-setup/auto_install.sh`    
Read and accept the AVS Device SDK license agreement.

6. You will be prompted enter your Alexa device details and asked whether you want the Sample App to run automatically when the Raspberry Pi boots.

7. Read and accept the Sensory license agreement.
Wait for the script to complete the installation. This can take some time.

8. As a final step, the script will open http://localhost:3000 in a browser on the Raspberry Pi. Enter your Amazon Developer credentials and close the browser window when prompted. (You won't have to do this if you already have a valid configuration file.)  
If you see a `400 Bad Request - HTTP` error it may be necessary to add http:// URLs to your device origins and return fields. To do this, go to your amazon developer AVS home page (https://developer.amazon.com/avs/home.html) and from `My products` select `manage` and then `security profile`. Now add http://localhost:3000 to the `Allowed origins` and http://localhost:3000/authresponse to the `Allowed return URLs`. Now refresh the browser window with the original error.

9. Enter `sudo reboot` to reboot the Raspberry Pi and complete the installation.

## Running the AVS SDK Sample App
The following commands will be available to run from a terminal:
- `avsrun` to run the Sample App.
- `avsauth` to re-authenticate your Alexa device details.
- `avsunit` to run the unit tests.
- `avssetup` to re-install the Sample App.
