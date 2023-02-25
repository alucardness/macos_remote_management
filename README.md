# DEP/Remote Management Workaround for macOS

If you did factory reset on your MacBook and want to pass without enrolling in profiles, that's the method for you. 

(Tested on M1)

<br>

- Start by creating an installation media of macOS Big Sur (use another computer with macOS or use a virtual machine, to create the bootable usb).

- Presuming your mac is turned off, plug the usb bootable media and long press and hold the power button until you see a sign loading startup options.

- Wait for the mac to recognize the usb for a couple of seconds and you should see Big Sur icon, click continue.

- When the installation has loaded, quit it from the menu. Go to disk utility and erase your mac drive.(If you had another version of macOS you will be prompted to restart and going though the activation mac window, it's safe to turn the network there) Go back to the installation and finish it. (You should be connected to internet, otherwise it won't finish).

- On the setup screen, when prompted to connect to a network, just hit continue (DO NOT CONNECT TO YOUR NETWORK) and a confirmation dialog would appear. All other settings, go as you pleased.

- Upon reaching your home screen, type the following commands in order, in the terminal:

        sudo nano /etc/hosts

    paste the following inside:

        0.0.0.0 iprofiles.apple.com
        0.0.0.0 mdmenrollment.apple.com
        0.0.0.0 deviceenrollment.apple.com

    proceed with:

        sudo profiles remove -all
        
    To check if everything is working, type the following:

        sudo profiles show -type enrollment

    If you see the following message 
    
    ## "Bad response from apsd: Connection interrupted
    ## Error fetching Device Enrollment configuration: We can't determine if this machine is DEP enabled.  Try again later.", 

    <br>
    
you are good to go...

<br>

## If the following was helpful, maybe 

<a href="https://www.buymeacoffee.com/alucardness"><img src="https://www.buymeacoffee.com/assets/img/guidelines/logo-mark-1.svg" width="50"/> Buy me a coffee</a>